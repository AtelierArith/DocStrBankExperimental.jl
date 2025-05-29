```
UnivariateFinite(support,
                 probs;
                 pool=nothing,
                 augmented=false,
                 ordered=false)
```

ベクトル `support` の要素を有限サポートとし、対応する確率をベクトル `probs` の要素とする離散的な単変量分布を構築します。あるいは、`probs` を生成された配列よりも1次元高い配列にすることで、`UnivariateFinite` 分布の抽象的な *配列* を構築します。

ここで「確率」という言葉は用語の乱用であり、確率が実際に1に合計される必要はありません。唯一の要件は、確率が `zero(T)` が定義されている共通の型 `T` を持つことです。特に、`UnivariateFinite` オブジェクトは、ラベル付きポイントの有限集合に対して任意の非負、符号付き、または複素数の測度を実装します。`UnivariateDistribution` は、`augment=true` オプションを使用して構築された場合（下記参照）やデータに `fit` された場合に、正当な確率測度となります。また、`UnivariateFinite` オブジェクト `d` の確率は非負であり、合計がゼロでない必要があり、そうでないと `rand(d)` は定義されず、解釈できません。

`pool` が指定されない限り、`support` は `AbstractVector{<:CategoricalValue}` 型である必要があり、すべての要素は同じカテゴリプールを共有していると仮定されます。このプールは `support` よりも大きい場合があります。

*重要.* 共通プールのすべてのレベルには関連する確率があり、指定された `support` にあるものだけではありません。ただし、これらの確率は常にゼロです（以下の例を参照）。

`probs` が行列の場合、`support` の各クラスに対して1列が必要です（または、`augment=true` の場合は1列少なくなります）。より一般的には、`probs` はサイズが `(n1, n2, ..., nk, c)` の配列であり、ここで `c = length(support)`（または、`augment=true` の場合は1列少なくなります）であり、コンストラクタはサイズが `(n1, n2, ..., nk)` の `UnivariateFinite` 分布の配列を返します。

```
using CategoricalDistributions, CategoricalArrays, Distributions
samples = categorical(['x', 'x', 'y', 'x', 'z'])
julia> Distributions.fit(UnivariateFinite, samples)
           UnivariateFinite{Multiclass{3}}
     ┌                                        ┐
   x ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 0.6
   y ┤■■■■■■■■■■■■ 0.2
   z ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 0.2
     └                                        ┘

julia> d = UnivariateFinite([samples[1], samples[end]], [0.1, 0.9])
UnivariateFinite{Multiclass{3}(x=>0.1, z=>0.9)
           UnivariateFinite{Multiclass{3}}
     ┌                                        ┐
   x ┤■■■■ 0.1
   z ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 0.9
     └                                        ┘

julia> rand(d, 3)
3-element Array{Any,1}:
 CategoricalValue{Symbol,UInt32} 'z'
 CategoricalValue{Symbol,UInt32} 'z'
 CategoricalValue{Symbol,UInt32} 'z'

julia> levels(samples)
3-element Array{Symbol,1}:
 'x'
 'y'
 'z'

julia> pdf(d, 'y')
0.0
```

### プールの指定

あるいは、`pool` が次のいずれかである場合、`support` は生の（非カテゴリカルな）要素のリストであることができます。

  * `CategoricalArray`、`CategoricalValue`、または `CategoricalPool` のいずれかで、`support` が `levels(pool)` の部分集合である場合
  * `missing` の場合、新しいカテゴリプールが作成され、`support` が唯一のレベルとなります。

最後のケースでは、プールが順序付きと見なされる場合は `ordered=true` を指定します。

```
julia> UnivariateFinite(['x', 'z'], [0.1, 0.9], pool=missing, ordered=true)
         UnivariateFinite{OrderedFactor{2}}
     ┌                                        ┐
   x ┤■■■■ 0.1
   z ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 0.9
     └                                        ┘

samples = categorical(['x', 'x', 'y', 'x', 'z'])
julia> d = UnivariateFinite(['x', 'z'], [0.1, 0.9], pool=samples)
     ┌                                        ┐
   x ┤■■■■ 0.1
   z ┤■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ 0.9
     └                                        ┘

julia> pdf(d, 'y') # allowed as `'y' in levels(samples)`
0.0

v = categorical(['x', 'x', 'y', 'x', 'z', 'w'])
probs = rand(100, 3)
probs = probs ./ sum(probs, dims=2)
julia> d1 = UnivariateFinite(['x', 'y', 'z'], probs, pool=v)
100-element UnivariateFiniteVector{Multiclass{4},Symbol,UInt32,Float64}:
 UnivariateFinite{Multiclass{4}}(x=>0.194, y=>0.3, z=>0.505)
 UnivariateFinite{Multiclass{4}}(x=>0.727, y=>0.234, z=>0.0391)
 UnivariateFinite{Multiclass{4}}(x=>0.674, y=>0.00535, z=>0.321)
   ⋮
 UnivariateFinite{Multiclass{4}}(x=>0.292, y=>0.339, z=>0.369)
```

### 確率の拡張

`augment=true` の場合、提供された配列は、配列の最後の次元に沿って提供された要素の前に適切な要素を挿入することによって拡張されます。これは、ユーザーがクラス `c2, c3, ..., cn` の確率のみを提供することを意味します。クラス `c1` の確率は、返される各 `UnivariateFinite` 分布が正当な確率分布となるように選択されます。

```julia
julia> UnivariateFinite([0.1, 0.2, 0.3], augment=true, pool=missing)
3-element UnivariateFiniteArray{Multiclass{2}, String, UInt8, Float64, 1}:
 UnivariateFinite{Multiclass{2}}(class_1=>0.9, class_2=>0.1)
 UnivariateFinite{Multiclass{2}}(class_1=>0.8, class_2=>0.2)
 UnivariateFinite{Multiclass{2}}(class_1=>0.7, class_2=>0.3)

d2 = UnivariateFinite(['x', 'y', 'z'], probs[:, 2:end], augment=true, pool=v)
julia> pdf(d1, levels(v)) ≈ pdf(d2, levels(v))
true
```

---

```
UnivariateFinite(prob_given_class; pool=nothing, ordered=false)
```

提供された辞書 `prob_given_class` のキーの集合を有限サポートとし、その値が対応する確率を指定する離散的な単変量分布を構築します。

辞書のキーに対する型要件は、上記の `support` の要素と同じですが、例外として、非カテゴリカルな要素（生のラベル）がキーとして使用される場合、`pool=...` を指定する必要があり、`missing` にはできません。

値（確率）がスカラーではなく配列である場合、`UnivariateFinite` 要素の抽象的な配列が作成され、配列と同じサイズになります。
