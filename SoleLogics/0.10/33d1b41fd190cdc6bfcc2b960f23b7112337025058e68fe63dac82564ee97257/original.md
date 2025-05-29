```
const DISJUNCTION = NamedConnective{:∨}()
const ∨ = DISJUNCTION
arity(::typeof(∨)) = 2
```

Logical disjunction. It can be typed by `\vee<tab>`.

See also [`NamedConnective`](@ref), [`Connective`](@ref).
