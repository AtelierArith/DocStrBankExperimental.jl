```
const BOX = NamedConnective{:□}()
const □ = BOX
arity(::typeof(□)) = 1
```

Logical box connective, typically interpreted as the modal universal quantifier. See [here](https://en.wikipedia.org/wiki/Modal_operator).

See also [`DIAMOND`](@ref), [`NamedConnective`](@ref), [`Connective`](@ref).
