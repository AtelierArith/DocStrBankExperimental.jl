```
mzero(M::MonadPlusClass)
(M::MonadPlusClass).mzero
```

Returns the monadic context of the zero element. (mzero :: MonadPlusClass M: M x)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mzero(Maybe) === Maybe.mzero === nothing
true
```
