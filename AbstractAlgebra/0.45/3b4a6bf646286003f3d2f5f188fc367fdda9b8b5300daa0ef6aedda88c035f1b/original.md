```
Fac{T <: RingElement}
```

Type for factored ring elements. The structure holds a unit of type `T` and is an iterable collection of `T => Int` pairs for the factors and exponents.

See [`unit(a::Fac)`](@ref), [`evaluate(a::Fac)`](@ref).
