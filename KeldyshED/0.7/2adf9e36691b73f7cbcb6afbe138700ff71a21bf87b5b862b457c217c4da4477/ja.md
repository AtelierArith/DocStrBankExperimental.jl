```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.ImaginaryTimeGrid,
    c_indices::Vector{Vector{Union{Int64, String}}},
    cdag_indices::Vector{Vector{Union{Int64, String}}};
    gf_filler
) -> Keldysh.ImaginaryTimeGF{ComplexF64, false}

```

行列値の単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

虚時間区間 $[0;-i\beta]$ において、与えられた $i$ のリストと $j$ のリストに対して、すべての可能な複合インデックスのペア $(i, j)$ に対して計算します（リストは同じ長さでなければなりません）。

## 引数

  * `ed`:           正確対角化オブジェクト。
  * `grid`:         虚時間区間の時間グリッド。
  * `c_indices`:    複合インデックス $i$ のリスト。
  * `cdag_indices`: 複合インデックス $j$ のリスト。
  * `gf_filler`:    [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
