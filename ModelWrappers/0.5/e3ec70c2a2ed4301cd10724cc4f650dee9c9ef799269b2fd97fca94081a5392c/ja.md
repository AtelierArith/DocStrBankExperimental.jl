```julia
struct ParameterInfo{R<:ModelWrappers.ReConstructor, U<:ModelWrappers.ReConstructor, T<:ModelWrappers.TransformConstructor}
```

パラメータ分布、変換、および制約に関する情報を含みます。

# フィールド

  * `reconstruct::ModelWrappers.ReConstructor`: パラメータのフラット化/非フラット化に関する情報を含みます
  * `reconstructᵤ::ModelWrappers.ReConstructor`: 制約のないパラメータを再構築するための情報を含みます - 非双射変換にとって重要です
  * `transform::ModelWrappers.TransformConstructor`: パラメータの制約および非制約に関する情報を含みます。
