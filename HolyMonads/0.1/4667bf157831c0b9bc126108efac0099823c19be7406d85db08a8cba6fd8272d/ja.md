```
monadtype(::Type{MT}) where {MT <: MonadClass}
monadtype(::MT) where {MT <: MonadClass}
(M::MT).monadtype
```

指定されたモナドクラスに対する対応するモナディックコンテキストタイプを返します。

# 例

```julia-repl
julia> using HolyMonads

juila> using HolyMonads.MaybeMonad

julia> monadtype(Maybe) === Maybe.monadtype === MaybeMonad.MaybeType
true
```
