```
Ball1{N, VN<:AbstractVector{N}} <: AbstractCentrallySymmetricPolytope{N}
```

1ノルム（マンハッタンノルムとも呼ばれる）におけるボールを表す型です。このボールは[交差多面体](https://en.wikipedia.org/wiki/Cross-polytope)としても知られています。

次の集合として定義されます。

$$
\mathcal{B}_1^n(c, r) = \{ x ∈ ℝ^n : ∑_{i=1}^n |c_i - x_i| ≤ r \},
$$

ここで、$c ∈ ℝ^n$はその中心、$r ∈ ℝ_+$は半径です。

### フィールド

  * `center` – 実ベクトルとしてのボールの中心
  * `radius` – スカラー（$≥ 0$）としてのボールの半径

### 例

平面における1ノルムの単位ボール：

```jldoctest ball1_constructor
julia> B = Ball1(zeros(2), 1.0)
Ball1{Float64, Vector{Float64}}([0.0, 0.0], 1.0)
julia> dim(B)
2
```

北方向のサポートベクトルを評価します：

```jldoctest ball1_constructor
julia> σ([0.0, 1.0], B)
2-element Vector{Float64}:
 0.0
 1.0
```
