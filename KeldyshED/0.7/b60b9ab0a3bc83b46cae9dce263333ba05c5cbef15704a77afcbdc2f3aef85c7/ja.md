```julia
computegf(
    ed::KeldyshED.EDCore,
    t1::Keldysh.BranchPoint,
    t2::Keldysh.BranchPoint,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}},
    β::Float64
) -> ComplexF64

```

単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

与えられた創造/消滅演算子の複合インデックス $i$ と $j$ に対して、与えられたコンター時間 $t_1$, $t_2$ で。

## 引数

  * `ed`:         正確対角化オブジェクト。
  * `t1`:         コンター時間 $t_1$。
  * `t2`:         コンター時間 $t_2$。
  * `c_index`:    複合インデックス $i$。
  * `cdag_index`: 複合インデックス $j$。
  * `β`:          逆温度 $\beta$。
