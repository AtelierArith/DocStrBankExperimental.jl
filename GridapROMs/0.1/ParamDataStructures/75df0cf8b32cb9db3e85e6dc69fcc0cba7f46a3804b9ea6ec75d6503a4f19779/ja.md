```
struct ParamSpace{P<:AbstractVector{<:AbstractVector},S<:SamplingStyle} <: AbstractSet{Realization}
  param_domain::P
  sampling_style::S
end
```

フィールド:

  * `param_domain`: パラメータの定義域
  * `sampling_style`: パラメータをサンプリングするための `param_domain` に基づく分布（デフォルトでは `HaltonSampling` に設定されています）
