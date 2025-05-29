```
mplus(M::MonadPlusClass, a, b)
(M::MonadPlusClass).mplus(a, b)
```

`a`と`b`を組み合わせた結果のモナディックコンテキストを返します。(mplus :: MonadPlusClass M: M x -> M x -> M x)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mplus(Maybe, Some(1), Some(2)) === Maybe.mplus(Some(1), Some(2)) === Some(1)
true
```
