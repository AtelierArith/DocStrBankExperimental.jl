```
mjoin(M::MonadClass, value)
(M::MonadClass).mjoin(value)
```

ネストされたモナディックコンテキストをフラット化します。引数 `value` はモナディックコンテキストでなければなりません。(mjoin :: MonadClass M: M (M x) -> M x)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mjoin(Maybe, Some(Some(1))) === Maybe.mjoin(Some(Some(1))) === Some(1)
true
```
