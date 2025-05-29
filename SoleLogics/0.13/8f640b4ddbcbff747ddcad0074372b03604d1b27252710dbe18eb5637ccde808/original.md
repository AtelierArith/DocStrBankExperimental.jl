```
struct Atom{V} <: AbstractAtom
    value::V
end
```

Simplest atom implementation, wrapping a `value`.

See also [`AbstractAtom`](@ref), [`value`](@ref), [`check`](@ref), [`SyntaxToken`](@ref).
