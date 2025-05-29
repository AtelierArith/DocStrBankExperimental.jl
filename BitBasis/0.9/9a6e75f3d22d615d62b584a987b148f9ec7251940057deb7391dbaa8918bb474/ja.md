```
bmask(::Type{T}) where T <: Integer -> zero(T)
bmask([T::Type], positions::Int...) -> T
bmask([T::Type], range::UnitRange{Int}) -> T
```

整数型 `T` のマスクを返します。`1` は `positions` または `range` に従ってマスクされた位置です。`T` を直接使用すると、空のマスク `0` が返されます。
