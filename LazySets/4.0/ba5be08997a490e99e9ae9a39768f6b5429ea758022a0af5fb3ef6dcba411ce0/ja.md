```
CartesianProduct{N, S1<:LazySet{N}, S2<:LazySet{N}} <: LazySet{N}
```

2つの集合の直積を表す型、すなわち集合

$$
Z = \{ z ∈ ℝ^{n + m} : z = (x, y),\qquad x ∈ X, y ∈ Y \}.
$$

もし $X ⊆ ℝ^n$ かつ $Y ⊆ ℝ^m$ であれば、$Z$ は $n+m$ 次元です。

### フィールド

  * `X` – 最初の集合
  * `Y` – 2番目の集合

### 注意事項

2つ以上の集合の直積の実装については、[`CartesianProductArray`](@ref)も参照してください。

`EmptySet` は `CartesianProduct` に対するほぼ吸収要素です（次元が調整されることを除いて）。

直積は凸性を保持します：集合の引数が凸であれば、その直積も凸です。

いくつかのドキュメント文字列では、「ブロック」という言葉が各ラップされた集合を示すために使用され、自然な順序で、すなわち直積 `cp` の最初のブロックは `cp.X` であり、2番目のブロックは `cp.Y` であると言います。

### 例

2つの集合 `X` と `Y` の直積は、`CartesianProduct(X, Y)` を使用するか、ショートカット表記 `X × Y` を使用して構築できます（*掛け算*記号を入力するには、`\times<tab>` と書きます）。

```jldoctest cartesianproduct_constructor
julia> I1 = Interval(0, 1);

julia> I2 = Interval(2, 4);

julia> I12 = I1 × I2;

julia> typeof(I12)
CartesianProduct{Float64, Interval{Float64}, Interval{Float64}}
```

ハイパーレクタングルは区間の直積であるため、`I12` を `Hyperrectangle` 型に変換できます：

```jldoctest cartesianproduct_constructor
julia> convert(Hyperrectangle, I12)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([0.5, 3.0], [0.5, 1.0])
```
