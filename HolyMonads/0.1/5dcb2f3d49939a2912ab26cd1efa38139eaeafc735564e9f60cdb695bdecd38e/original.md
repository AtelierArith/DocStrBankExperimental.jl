```
MonadClass(::Type{T}) where {T}
MonadClass(::T) where {T}
```

Returns the corresponding monad class for specified monad type.

# Example

```julia-repl
julia> using HolyMonads

juila> using HolyMonads.MaybeMonad

julia> MonadClass(Some(1)) === MonadClass(Nothing) === Maybe
true
```
