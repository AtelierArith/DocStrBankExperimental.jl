```
evaluate(
    A::ExaFMM{F},
    x::Vector{F},
    fmmoptions::ModifiedHelmholtzFMMOptions{I, F}
) where {I, F <: Real}
```

Evaluates prebuild FMM structure `A` for new values `x`.

# Arguments

  * `A::ExaFMM{F}`: ExaFMM structure with pointers to all allocated variables.
  * `x::Vector{F}`: Values of for example the charge at each source location.
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, F}`: Julia modified-Helmoltz-initializer for setup function, used as identifier.
