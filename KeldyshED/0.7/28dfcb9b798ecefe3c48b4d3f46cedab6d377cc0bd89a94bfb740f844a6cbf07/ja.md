```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.FullTimeGrid,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}};
    gf_filler
) -> Keldysh.TimeInvariantFullTimeGF{ComplexF64, true}

```

単一粒子ケルディシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

与えられた生成/消滅演算子の複合インデックス $i$ と $j$ に対して、3枝のコンスタンティノフ-ペレルの輪郭上で計算します。

## 引数

  * `ed`:         正確対角化オブジェクト。
  * `grid`:       3枝輪郭上の時間グリッド。
  * `c_index`:    複合インデックス $i$。
  * `cdag_index`: 複合インデックス $j$。
  * `gf_filler`:  [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
