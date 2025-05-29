```
∂(expr::JuMP.AbstractJuMPScalar, pref1::GeneralVariableRef[, ....]
  )::Union{JuMP.AbstractJuMPScalar, Float64}
```

This serves as a convenient unicode wrapper for [`deriv`](@ref). The `∂` is  produced via `\partial`.
