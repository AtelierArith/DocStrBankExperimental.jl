```
monadtype(::Type{MT}) where {MT <: MonadClass}
monadtype(::MT) where {MT <: MonadClass}
(M::MT).monadtype
```

Returns the corresponding monadic context type for specified monad class.

# Example

```julia-repl
julia> using HolyMonads

juila> using HolyMonads.MaybeMonad

julia> monadtype(Maybe) === Maybe.monadtype === MaybeMonad.MaybeType
true
```
