```
const IMPLICATION = NamedConnective{:→}()
const → = IMPLICATION
arity(::typeof(→)) = 2
```

Logical implication. It can be typed by `\to<tab>`.

See also [`NamedConnective`](@ref), [`Connective`](@ref).
