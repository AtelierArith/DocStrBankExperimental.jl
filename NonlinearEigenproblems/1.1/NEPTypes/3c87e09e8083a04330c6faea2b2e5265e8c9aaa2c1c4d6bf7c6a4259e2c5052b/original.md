```
abstract type Errmeasure; end
```

Concrete subtypes of `Errmeasure` represent specific ways of measuring the error of an eigenpair. NEP-solvers take such an object as input. As a NEP-solver user, you use the type as follows

```julia
julia> quasinewton(nep,errmeasure=ResidualErrmeasure(nep))
```

User-specified ways of measuring error can be given by creating a new subtype of `Errmeasure` and using it as a `errmeasure` keyword. You need to specify the way to measure the error in the method `estimate_error`.

Note that in practice a `Function` can essentially be used instead of a `Errmeasure`-object, which is a simple way to have user-defined error measures. See [`ErrmeasureType`](@ref).

See also: [`ErrmeasureType`](@ref), [`DefaultErrmeasure`](@ref), [`ResidualErrmeasure`](@ref), [`StandardSPMFErrmeasure`](@ref), [`estimate_error`](@ref), [`EigvalReferenceErrmeasure`](@ref).
