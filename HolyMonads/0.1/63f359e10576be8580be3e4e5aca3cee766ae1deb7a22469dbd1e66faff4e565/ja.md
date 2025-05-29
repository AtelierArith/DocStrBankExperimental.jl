```
mzero(M::MonadPlusClass)
(M::MonadPlusClass).mzero
```

ゼロ要素のモナディックコンテキストを返します。(mzero :: MonadPlusClass M: M x)

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> mzero(Maybe) === Maybe.mzero === nothing
true
```
