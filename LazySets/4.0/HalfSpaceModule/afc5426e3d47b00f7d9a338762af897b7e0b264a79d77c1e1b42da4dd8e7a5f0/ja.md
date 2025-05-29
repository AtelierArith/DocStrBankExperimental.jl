# 拡張ヘルプ

```
project(H::HalfSpace, block::AbstractVector{Int}; [kwargs...])
```

### アルゴリズム

`H` の制約のない次元が `block` 変数の部分集合である場合、投影は `H` の法線方向に適用されます。そうでない場合、投影は全体集合の結果になります。

後者は次のように見ることができます。一般性を失うことなく、単一の制約された次元 $xₖ$ を投影することを考えます（複数の次元を投影することは、1つの次元を繰り返し投影することでモデル化できます）。投影を存在量化された線形制約として書くことができます：

$$
    ∃xₖ: a₁x₁ + … + aₖxₖ + … + aₙxₙ ≤ b
$$

$$
aₖ ≠ 0
$$

であるため、他の変数の任意の評価に対して制約を満たす $xₖ$ の値は常に存在します。

### 例

半空間 $x + y + 0⋅z ≤ 1$ を考えます。その周囲の次元は `3` です。変数のブロック `[1, 2, 3]` を使用した三次元での（自明な）投影は次のとおりです：

```jldoctest project_halfspace
julia> H = HalfSpace([1.0, 1.0, 0.0], 1.0)
HalfSpace{Float64, Vector{Float64}}([1.0, 1.0, 0.0], 1.0)

julia> project(H, [1, 2, 3])
HalfSpace{Float64, Vector{Float64}}([1.0, 1.0, 0.0], 1.0)
```

次元 `1` と `2` のみを投影する：

```jldoctest project_halfspace
julia> project(H, [1, 2])
HalfSpace{Float64, Vector{Float64}}([1.0, 1.0], 1.0)
```

便利のために、`project(H, constrained_dimensions(H))` を使用して、制約のある次元に投影された半空間を返すことができます：

```jldoctest project_halfspace
julia> project(H, constrained_dimensions(H))
HalfSpace{Float64, Vector{Float64}}([1.0, 1.0], 1.0)
```

制約された次元が投影されると、投影に対応する次元の全体集合が得られます。

```jldoctest project_halfspace
julia> project(H, [1, 3])
Universe{Float64}(2)

julia> project(H, [1])
Universe{Float64}(1)
```
