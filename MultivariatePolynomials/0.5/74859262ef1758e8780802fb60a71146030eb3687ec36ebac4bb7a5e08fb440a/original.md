```
ordinary_variable(x::Union{AbstractVariable, AbstractVector{<:AbstractVariable}})
```

Given some (complex-valued) variable that was transformed by conjugation, taking its real part, or taking its imaginary part, return the original variable as it was defined by the user.

See also [`conj`](@ref), [`real`](@ref), [`imag`](@ref).
