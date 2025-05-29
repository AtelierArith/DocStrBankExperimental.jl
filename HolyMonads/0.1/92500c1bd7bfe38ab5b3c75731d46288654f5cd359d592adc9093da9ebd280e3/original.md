```
mplus(M::MonadPlusClass, a, b)
(M::MonadPlusClass).mplus(a, b)
```

Returns the monadic context of the result of combining `a` and `b`. (mplus :: MonadPlusClass M: M x -> M x -> M x)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mplus(Maybe, Some(1), Some(2)) === Maybe.mplus(Some(1), Some(2)) === Some(1)
true
```
