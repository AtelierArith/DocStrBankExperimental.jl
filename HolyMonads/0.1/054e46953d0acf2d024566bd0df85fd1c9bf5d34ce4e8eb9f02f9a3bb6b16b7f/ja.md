```
unit(::MT, value) where {MT <: MonadClass}
(M::MonadClass).unit(value)
```

指定された値のモナディックコンテキストを返します。   (unit :: MonadClass M: x -> M x)   (別名 `return` または `pure`)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> unit(Maybe, 1) === Maybe.unit(1) === Some(1)
true
```
