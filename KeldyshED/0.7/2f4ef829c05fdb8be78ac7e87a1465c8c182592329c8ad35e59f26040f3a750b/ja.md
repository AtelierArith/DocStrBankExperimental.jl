```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.FullTimeGrid,
    c_cdag_index_pairs::Vector{Tuple{Vector{Union{Int64, String}}, Vector{Union{Int64, String}}}};
    gf_filler
) -> Vector{Keldysh.TimeInvariantFullTimeGF{ComplexF64, true}}

```

複数の単一粒子ケルディシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

与えられた生成/消滅演算子の複合インデックス $i$ と $j$ に対して、3本のブランチのコンスタンティノフ-ペレル'コンター上で。

## 引数

  * `ed`:                 正確対角化オブジェクト。
  * `grid`:               3本のブランチコンター上の時間グリッド。
  * `c_cdag_index_pairs`: 複合インデックスペアのリスト $(i, j)$。
  * `gf_filler`:          [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
