```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.KeldyshTimeGrid,
    c_cdag_index_pairs::Vector{Tuple{Vector{Union{Int64, String}}, Vector{Union{Int64, String}}}},
    β::Float64;
    gf_filler
) -> Vector{Keldysh.TimeInvariantKeldyshTimeGF{ComplexF64, true}}

```

複数の単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

与えられた生成/消滅演算子の複合インデックス $i$ と $j$ に対して、逆温度 $\beta$ でデカップリングされた初期熱状態の下で、2ブランチケルディッシュコンター上で計算します。

## 引数

  * `ed`:                 正確対角化オブジェクト。
  * `grid`:               2ブランチコンター上の時間グリッド。
  * `c_cdag_index_pairs`: 複合インデックスペアのリスト $(i, j)$。
  * `β`:                  逆温度 $\beta$。
  * `gf_filler`:          [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
