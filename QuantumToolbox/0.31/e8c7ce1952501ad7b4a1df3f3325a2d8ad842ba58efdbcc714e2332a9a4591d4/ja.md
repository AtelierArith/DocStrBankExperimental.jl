```
entropy_conditional(ρAB::QuantumObject, selB; kwargs...)
```

サブシステム $B$ に関する [条件付き量子エントロピー](https://en.wikipedia.org/wiki/Conditional_quantum_entropy) を計算します: $S(A|B) = S(\hat{\rho}_{AB}) - S(\hat{\rho}_{B})$。

ここで、$S$ は [フォン・ノイマンエントロピー](https://en.wikipedia.org/wiki/Von_Neumann_entropy) であり、$\hat{\rho}_{AB}$ は全体のシステムの密度行列、$\hat{\rho}_B = \textrm{Tr}_A \left[ \hat{\rho}_{AB} \right]$ です。

# 注意事項

  * `ρAB` は [`Ket`](@ref) または [`Operator`](@ref) のいずれかです。
  * `selB` は `ρAB.dimensions` におけるサブシステム `B` のインデックスを指定します。 [`ptrace`](@ref) も参照してください。
  * `kwargs` はフォン・ノイマンエントロピーを計算するためのキーワード引数です。 [`entropy_vn`](@ref) も参照してください。
