```
partial_transpose(ρ::QuantumObject, mask::Vector{Bool})
```

密度行列 $\rho$ の部分転置を返します。ここで、`mask` は `ρ.dims` の長さと等しい長さの配列/ベクトルです。`mask` の要素はブール値（`true` または `false`）で、対応するサブシステムを転置するかどうかを示します。

# 引数

  * `ρ::QuantumObject`: 密度行列（`ρ.type` は [`Operator`](@ref) でなければなりません）。
  * `mask::Vector{Bool}`: 転置すべきサブシステムを選択するブールベクトル。

# 戻り値

  * `ρ_pt::QuantumObject`: 選択されたサブシステムが転置された密度行列。
