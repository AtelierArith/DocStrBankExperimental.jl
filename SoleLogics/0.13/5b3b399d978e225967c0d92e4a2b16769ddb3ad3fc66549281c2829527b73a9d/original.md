```
const CONJUNCTION = NamedConnective{:∧}()
const ∧ = CONJUNCTION
arity(::typeof(∧)) = 2
```

Logical conjunction. It can be typed by `\wedge<tab>`.

See also [`NamedConnective`](@ref), [`Connective`](@ref).
