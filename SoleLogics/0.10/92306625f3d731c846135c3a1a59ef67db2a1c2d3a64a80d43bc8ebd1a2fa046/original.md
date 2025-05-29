```
const NEGATION = NamedConnective{:¬}()
const ¬ = NEGATION
arity(::typeof(¬)) = 1
```

Logical negation (also referred to as complement). It can be typed by `\neg<tab>`.

See also [`NamedConnective`](@ref), [`Connective`](@ref).
