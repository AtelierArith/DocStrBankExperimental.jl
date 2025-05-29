```
UnivariateFinite(
    support,
    probs;
    pool=nothing,
    augmented=false,
    ordered=false
)
```

ベクトル `support` の要素を有限サポートとし、対応する確率をベクトル `probs` の要素とする離散的な一変量分布を構築します。あるいは、`probs` を生成された配列よりも1次元高い配列にすることで、`UnivariateFinite` 分布の抽象的な *配列* を構築します。

ここで「確率」という言葉は用語の誤用であり、確率が実際に1に合計される必要はなく、非負であることだけが求められます。したがって、`UnivariateFinite` オブジェクトは、ラベル付き点の有限集合に対する任意の非負測度を実装します。`augment=true` オプションを使用して構築されるとき、またはデータに `fit` されるとき、`UnivariateDistribution` は本物の確率測度になります。

`pool` が指定されない限り、`support` は `AbstractVector{<:CategoricalValue}` 型である必要があり、すべての要素は同じカテゴリプールを共有していると仮定されます。このプールは `support` よりも大きい場合があります。

*重要。* 共通プールのすべてのレベルには関連する確率があり、指定された `support` にあるものだけではありません。ただし、これらの確率は常にゼロです（以下の例を参照）。

`probs` が行列の場合、`support` の各クラスに対して1列が必要です（または、`augment=true` の場合は1列少なくなります）。より一般的には、`probs` はサイズが `(n1, n2, ..., nk, c)` の配列であり、ここで `c = length(support)`（または、`augment=true` の場合は1つ少なくなります）であり、コンストラクタはサイズ `(n1, n2, ..., nk)` の `UnivariateFinite` 分布の配列を返します。

## 例

```julia-repl
julia> v = categorical(["x", "x", "y", "x", "z"])
5-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "x"
 "y"
 "x"
 "z"

julia> UnivariateFinite(classes(v), [0.2, 0.3, 0.5])
UnivariateFinite{Multiclass{3}}(x=>0.2, y=>0.3, z=>0.5)

julia> d = UnivariateFinite([v[1], v[end]], [0.1, 0.9])
UnivariateFinite{Multiclass{3}}(x=>0.1, z=>0.9)

julia> rand(d, 3)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "z"
 "x"

julia> levels(d)
3-element Vector{String}:
 "x"
 "y"
 "z"

julia> pdf(d, "y")
0.0

```

### プールの指定

あるいは、`pool` が次のいずれかである場合、`support` は生の（非カテゴリカルな）要素のリストであることができます。

  * `CategoricalArray`、`CategoricalValue`、または `CategoricalPool` のいずれかで、`support` が `levels(pool)` の部分集合である場合
  * `missing` の場合、この場合は `support` を唯一のレベルとする新しいカテゴリプールが作成されます。

最後のケースでは、プールが順序付きと見なされる場合は `ordered=true` を指定します。

```julia-repl
julia> UnivariateFinite(["x", "z"], [0.1, 0.9], pool=missing, ordered=true)
UnivariateFinite{OrderedFactor{2}}(x=>0.1, z=>0.9)

julia> d = UnivariateFinite(["x", "z"], [0.1, 0.9], pool=v) # v は上で定義された
UnivariateFinite{Multiclass{3}}(x=>0.1, z=>0.9)

julia> pdf(d, "y") # `"y" in levels(v)` なので許可される
0.0

julia> v = categorical(["x", "x", "y", "x", "z", "w"])
6-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "x"
 "x"
 "y"
 "x"
 "z"
 "w"

julia> probs = rand(100, 3); probs = probs ./ sum(probs, dims=2);

julia> UnivariateFinite(["x", "y", "z"], probs, pool=v)
100-element UnivariateFiniteVector{Multiclass{4}, String, UInt32, Float64}:
 UnivariateFinite{Multiclass{4}}(x=>0.194, y=>0.3, z=>0.505)
 UnivariateFinite{Multiclass{4}}(x=>0.727, y=>0.234, z=>0.0391)
 UnivariateFinite{Multiclass{4}}(x=>0.674, y=>0.00535, z=>0.321)
 ⋮
 UnivariateFinite{Multiclass{4}}(x=>0.292, y=>0.339, z=>0.369)
```

### 確率の拡張

`augment=true` の場合、提供された配列は、配列の最後の次元に沿って提供された要素の前に適切な要素を挿入することによって拡張されます。これは、ユーザーがクラス `c2, c3, ..., cn` の確率のみを提供することを意味します。クラス `c1` の確率は、返される配列内の各 `UnivariateFinite` 分布が本物の確率分布になるように選ばれます。

---

```
UnivariateFinite(prob_given_class; pool=nothing, ordered=false)
```

提供された辞書 `prob_given_class` のキーの集合を有限サポートとし、その値が対応する確率を指定する離散的な一変量分布を構築します。

辞書のキーに対する型要件は、上記の `support` の要素と同じですが、1つの例外があります：非カテゴリカルな要素（生のラベル）がキーとして使用される場合、`pool=...` を指定する必要があり、`missing` にはできません。

値（確率）がスカラーではなく配列である場合、`UnivariateFinite` 要素の抽象配列が作成され、配列と同じサイズになります。
