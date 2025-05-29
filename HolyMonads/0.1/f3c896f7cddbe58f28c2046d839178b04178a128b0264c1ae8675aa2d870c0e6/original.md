```
mjoin(M::MonadClass, value)
(M::MonadClass).mjoin(value)
```

Flattens the nested monadic context.  The argument `value` must be a monadic context. (mjoin :: MonadClass M: M (M x) -> M x)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mjoin(Maybe, Some(Some(1))) === Maybe.mjoin(Some(Some(1))) === Some(1)
true
```
