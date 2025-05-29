```
BallInf{N, VN<:AbstractVector{N}} <: AbstractHyperrectangle{N}
```

無限ノルムのボールを表す型。

### フィールド

  * `center` – ボールの中心を表す実ベクトル
  * `radius` – ボールの半径を表す実スカラー ($≥ 0$)

### ノート

数学的に、無限ノルムのボールは次の集合として定義されます。

$$
\mathcal{B}_∞^n(c, r) = \{ x ∈ ℝ^n : ‖ x - c ‖_∞ ≤ r \},
$$

ここで $c ∈ ℝ^n$ はその中心であり、$r ∈ ℝ_+$ はその半径です。ここで $‖ ⋅ ‖_∞$ は無限ノルムを示し、任意の $x ∈ ℝ^n$ に対して $‖ x ‖_∞ = \max\limits_{i=1,…,n} \vert x_i \vert$ と定義されます。

### 例

二次元の単位ボールを構築し、正の $x=y$ 方向に沿った支持関数を計算します：

```jldoctest
julia> B = BallInf(zeros(2), 1.0)
BallInf{Float64, Vector{Float64}}([0.0, 0.0], 1.0)

julia> dim(B)
2

julia> ρ([1.0, 1.0], B)
2.0
```
