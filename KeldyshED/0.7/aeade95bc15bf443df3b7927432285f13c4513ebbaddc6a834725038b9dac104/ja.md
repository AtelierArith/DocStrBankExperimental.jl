```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.KeldyshTimeGrid,
    c_indices::Vector{Vector{Union{Int64, String}}},
    cdag_indices::Vector{Vector{Union{Int64, String}}},
    β::Float64;
    gf_filler
) -> Keldysh.TimeInvariantKeldyshTimeGF{ComplexF64, false}

```

行列値の単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

すべての可能な化合物インデックスのペア $(i, j)$ に対して、$i$ のリストと $j$ のリストが与えられたときに、2分岐ケルディッシュコンター上で計算します（リストは同じ長さでなければなりません）。

## 引数

  * `ed`:           正確対角化オブジェクト。
  * `grid`:         2分岐コンター上の時間グリッド。
  * `c_indices`:    化合物インデックス $i$ のリスト。
  * `cdag_indices`: 化合物インデックス $j$ のリスト。
  * `β`:            逆温度 $\beta$。
  * `gf_filler`:    [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
