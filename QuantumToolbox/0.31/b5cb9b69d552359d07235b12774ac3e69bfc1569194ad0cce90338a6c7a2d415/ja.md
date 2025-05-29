```
entropy_mutual(ρAB::QuantumObject, selA, selB; kwargs...)
```

サブシステム $A$ と $B$ の間の [量子相互情報量](https://en.wikipedia.org/wiki/Quantum_mutual_information) $I(A:B) = S(\hat{\rho}_A) + S(\hat{\rho}_B) - S(\hat{\rho}_{AB})$ を計算します。

ここで、$S$ は [フォン・ノイマンエントロピー](https://en.wikipedia.org/wiki/Von_Neumann_entropy) であり、$\hat{\rho}_{AB}$ は全体のシステムの密度行列、$\hat{\rho}_A = \textrm{Tr}_B \left[ \hat{\rho}_{AB} \right]$、$\hat{\rho}_B = \textrm{Tr}_A \left[ \hat{\rho}_{AB} \right]$ です。

# 注意事項

  * `ρAB` は [`Ket`](@ref) または [`Operator`](@ref) のいずれかです。
  * `selA` は `ρAB.dimensions` におけるサブシステム `A` のインデックスを指定します。詳細は [`ptrace`](@ref) を参照してください。
  * `selB` は `ρAB.dimensions` におけるサブシステム `B` のインデックスを指定します。詳細は [`ptrace`](@ref) を参照してください。
  * `kwargs` はフォン・ノイマンエントロピーを計算するためのキーワード引数です。詳細は [`entropy_vn`](@ref) を参照してください。
