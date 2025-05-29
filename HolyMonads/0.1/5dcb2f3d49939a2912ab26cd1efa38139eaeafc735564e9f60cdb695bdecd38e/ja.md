```
MonadClass(::Type{T}) where {T}
MonadClass(::T) where {T}
```

指定されたモナドタイプに対応するモナドクラスを返します。

# 例

```julia-repl
julia> using HolyMonads

julia> using HolyMonads.MaybeMonad

julia> MonadClass(Some(1)) === MonadClass(Nothing) === Maybe
true
```
