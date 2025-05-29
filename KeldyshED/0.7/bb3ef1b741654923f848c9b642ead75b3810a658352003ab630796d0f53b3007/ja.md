```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.KeldyshTimeGrid,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}},
    β::Float64;
    gf_filler
) -> Keldysh.TimeInvariantKeldyshTimeGF{ComplexF64, true}

```

単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

与えられた生成/消滅演算子の複合インデックス $i$ と $j$ に対して、逆温度 $\beta$ で分離された初期熱状態の下で、2枝ケルディッシュコンター上で計算します。

## 引数

  * `ed`:         正確対角化オブジェクト。
  * `grid`:       2枝コンター上の時間グリッド。
  * `c_index`:    複合インデックス $i$。
  * `cdag_index`: 複合インデックス $j$。
  * `β`:          逆温度 $\beta$。
  * `gf_filler`:  [`アルゴリズムセレクタ`](@ref AbstractGFFiller) グリーン関数計算用。
