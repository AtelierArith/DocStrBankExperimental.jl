```
unit(::MT, value) where {MT <: MonadClass}
(M::MonadClass).unit(value)
```

Returns the monadic context of the specified value.   (unit :: MonadClass M: x -> M x)   (a.k.a. `return` or `pure`)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> unit(Maybe, 1) === Maybe.unit(1) === Some(1)
true
```
