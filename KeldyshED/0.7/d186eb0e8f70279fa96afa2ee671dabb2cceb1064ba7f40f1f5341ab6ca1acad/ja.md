```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.ImaginaryTimeGrid,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}};
    gf_filler
) -> Keldysh.ImaginaryTimeGF{ComplexF64, true}

```

単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

与えられた生成/消滅演算子の複合インデックス $i$ と $j$ に対して、虚時間区間 $[0;-i\beta]$ で計算します。

## 引数

  * `ed`:         正確対角化オブジェクト。
  * `grid`:       虚時間区間の時間グリッド。
  * `c_index`:    複合インデックス $i$。
  * `cdag_index`: 複合インデックス $j$。
  * `gf_filler`:  [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
