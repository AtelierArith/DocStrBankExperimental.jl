```julia
computegf(
    ed::KeldyshED.EDCore,
    t1::Keldysh.BranchPoint,
    t2::Keldysh.BranchPoint,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}};
    en,
    ρ
)

```

単一粒子ケルディッシュグリーン関数を計算します

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

与えられたコンター時間 $t_1$, $t_2$ に対して、生成/消滅演算子の複合インデックス $i$ と $j$ に対して。このメソッドは、密度行列 $\hat\rho$ がすでに計算されている場合に便利です。

## 引数

  * `ed`:         正確対角化オブジェクト。
  * `t1`:         コンター時間 $t_1$。
  * `t2`:         コンター時間 $t_2$。
  * `c_index`:    複合インデックス $i$。
  * `cdag_index`: 複合インデックス $j$。
  * `en`:         [`energies()`](@ref KeldyshED.energies) によって返されるシステムのエネルギーレベル。
  * `ρ`           [`density_matrix()`](@ref KeldyshED.density_matrix) によって返される密度行列 $\hat\rho$。
