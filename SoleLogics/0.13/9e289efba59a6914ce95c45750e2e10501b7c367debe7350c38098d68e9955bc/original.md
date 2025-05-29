```
const DIAMOND = NamedConnective{:◊}()
const ◊ = DIAMOND
ismodal(::typeof(◊)) = true
arity(::typeof(◊)) = 1
```

Logical diamond connective, typically interpreted as the modal existential quantifier. See [here](https://en.wikipedia.org/wiki/Modal_operator).

See also [`BOX`](@ref), [`NamedConnective`](@ref), [`Connective`](@ref).
