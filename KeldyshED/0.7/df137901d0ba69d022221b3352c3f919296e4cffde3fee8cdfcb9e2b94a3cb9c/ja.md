```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.FullTimeGrid,
    c_indices::Vector{Vector{Union{Int64, String}}},
    cdag_indices::Vector{Vector{Union{Int64, String}}};
    gf_filler
) -> Keldysh.TimeInvariantFullTimeGF{ComplexF64, false}

```

行列値の単一粒子ケルディシュ・グリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

すべての可能な化合インデックスのペア $(i, j)$ に対して、$i$ のリストと $j$ のリストが与えられたときに、3ブランチのコンスタンティノフ・ペレ contour 上で計算します（リストは同じ長さでなければなりません）。

## 引数

  * `ed`:           正確対角化オブジェクト。
  * `grid`:         3ブランチコンター上の時間グリッド。
  * `c_indices`:    化合インデックス $i$ のリスト。
  * `cdag_indices`: 化合インデックス $j$ のリスト。
  * `gf_filler`:    [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
