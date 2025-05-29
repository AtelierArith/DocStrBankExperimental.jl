```
∂(expr::JuMP.AbstractJuMPScalar, pref1::GeneralVariableRef[, ....]
  )::Union{JuMP.AbstractJuMPScalar, Float64}
```

これは[`deriv`](@ref)の便利なユニコードラッパーとして機能します。`∂`は`\partial`を介して生成されます。
