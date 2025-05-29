```
evaluate(
    A::ExaFMM{F},
    x::Vector{F},
    fmmoptions::LaplaceFMMOptions{I}
) where {I, F <: Real}
```

Evaluates prebuild FMM structure `A` for new values `x`.

# Arguments

  * `A::ExaFMM{F}`: ExaFMM structure with pointers to all allocated variables.
  * `x::Vector{F}`: Values of for example the charge at each source location.
  * `fmmoptions::LaplaceFMMOptions{I}`: Julia Laplace-initializer for setup function, used as identifier.
