```
Translation{N, S<:LazySet{N}, VN<:AbstractVector{N}}
    <: AbstractAffineMap{N, S}
```

遅延翻訳を表す型。

ベクトル `v` に沿った集合 `X` の翻訳は、次のマップです：

$$
x ↦ x + v,\qquad x ∈ X
$$

翻訳は、線形マップ $A$ が単位行列であり、翻訳ベクトル $b$ が $v$ である場合のアフィンマップ $A x + b, x ∈ X$ の特別なケースです。

### フィールド

  * `X` – 集合
  * `v` – 翻訳を定義するベクトル

### 注意

翻訳は凸性を保持します：もし `X` が凸であれば、`X` の任意の翻訳も凸です。

### 例

```jldoctest translation
julia> X = BallInf([2.0, 2.0, 2.0], 1.0);

julia> v = [1.0, 0.0, 0.0]; # 次元1に沿った翻訳

julia> tr = Translation(X, v);

julia> typeof(tr)
Translation{Float64, BallInf{Float64, Vector{Float64}}, Vector{Float64}}

julia> tr.X
BallInf{Float64, Vector{Float64}}([2.0, 2.0, 2.0], 1.0)

julia> tr.v
3-element Vector{Float64}:
 1.0
 0.0
 0.0
```

和演算子 `+` とミンコフスキー和演算子 `⊕` は翻訳を作成するためにオーバーロードされています：

```jldoctest translation
julia> X + v == X ⊕ v == Translation(X, v)
true
```

翻訳の翻訳は即座に行われます：

```jldoctest translation
julia> tr = (X + v) + v
Translation{Float64, BallInf{Float64, Vector{Float64}}, Vector{Float64}}(BallInf{Float64, Vector{Float64}}([2.0, 2.0, 2.0], 1.0), [2.0, 0.0, 0.0])

julia> tr.v
3-element Vector{Float64}:
 2.0
 0.0
 0.0
```

翻訳の次元は `dim` 関数を使って取得できます：

```jldoctest translation
julia> dim(tr)
3
```

ベクトル `d` に沿ったサポートベクトル（またはサポート関数）には、それぞれ `σ` と `ρ` を使用します：

```jldoctest translation
julia> σ([1.0, 0.0, 0.0], tr)
3-element Vector{Float64}:
 5.0
 2.0
 2.0

julia> ρ([1.0, 0.0, 0.0], tr)
5.0
```

詳細については、これらの関数のドキュメントを参照してください。

`an_element` 関数は翻訳の要素を取得するのに便利です：

```jldoctest translation
julia> e = an_element(tr)
3-element Vector{Float64}:
 4.0
 2.0
 2.0
```

翻訳の遅延線形マップはアフィンマップであり、次の簡略化ルールが適用されます：$M * (X ⊕ v) = (M * X) ⊕ (M * v)$：

```jldoctest translation
julia> using LinearAlgebra: I

julia> M = Matrix(2.0I, 3, 3);

julia> Q = M * tr;

julia> Q isa AffineMap && Q.M == M && Q.X == tr.X && Q.v == 2 * tr.v
true
```

翻訳が空であるかどうかを確認するには `isempty` メソッドを使用します：

```jldoctest translation
julia> isempty(tr)
false
```

ポリヘドラル集合の翻訳の制約リスト（`constraints_list` が利用可能な集合）は、遅延翻訳から計算できます：

```jldoctest translation
julia> constraints_list(tr)
6-element Vector{HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}}:
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([1.0, 0.0, 0.0], 5.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 1.0, 0.0], 3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 0.0, 1.0], 3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([-1.0, 0.0, 0.0], -3.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, -1.0, 0.0], -1.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 0.0, -1.0], -1.0)
```
