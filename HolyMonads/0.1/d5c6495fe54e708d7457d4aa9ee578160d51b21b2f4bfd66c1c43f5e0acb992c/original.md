```
fmap(f::Callable, M::MonadClass, t)
(M::MonadClass).fmap(f, t)
```

Returns the monadic context of the result of applying `f` to the value in the monadic context `t`.   You can use Julia's `do` syntax to pass the function `f` as a block. (fmap :: MonadClass M: (x -> y) -> M x -> M y) (a.k.a. `flatmap`)

# Example

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> fmap(Maybe, Some(1)) do x
           x + 1
       end === Maybe.fmap(x -> x + 1, Some(1)) === Some(2)
true
```
