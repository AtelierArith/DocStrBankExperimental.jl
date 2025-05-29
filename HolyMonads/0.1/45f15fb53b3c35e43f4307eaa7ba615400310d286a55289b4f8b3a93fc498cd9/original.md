```
mbind(f::Callable, M::MonadClass, t)
(M::MT).mbind(f, t)
```

Returns the monadic context of the result of applying `f` to the value in the monadic context `t`. You can use Julia's `do` syntax to pass the function `f` as a block. (mbind :: MonadClass M: (x -> M y) -> M x -> M y) (a.k.a. `bind`)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mbind(Maybe, Some(1)) do x
           unit(Maybe, x + 1)
       end === Maybe.mbind(x -> Maybe.unit(x + 1), Some(1)) === Some(2)
true
```
