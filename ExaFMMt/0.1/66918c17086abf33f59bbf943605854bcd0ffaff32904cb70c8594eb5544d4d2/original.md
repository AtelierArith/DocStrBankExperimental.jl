```
evaluate(
    A::ExaFMM{C},
    x::Vector{C},
    fmmoptions::HelmholtzFMMOptions{I, C}
) where {I, C <: Complex}
```

Evaluates prebuild FMM structure `A` for new values `x`.

# Arguments

  * `A::ExaFMM{C}`: ExaFMM structure with pointers to all allocated variables.
  * `x::Vector{C}`: Values of for example the charge at each source location.
  * `fmmoptions::HelmholtzFMMOptions{I, C}`: Julia Helmoltz-initializer for setup function, used as identifier.
