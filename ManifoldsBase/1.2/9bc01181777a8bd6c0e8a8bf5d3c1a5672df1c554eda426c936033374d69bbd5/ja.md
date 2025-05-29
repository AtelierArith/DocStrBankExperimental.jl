```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

[`InverseProductRetraction`](@ref) を返します。二つ以上の [`AbstractInverseRetractionMethod`](@ref) の場合、もしそのうちの一つが [`InverseProductRetraction`](@ref) 自体であれば、もう一方は前に追加されます（`r` が積の場合）または後に追加されます（`s` の場合）。もし両方が [`InverseProductRetraction`](@ref) であれば、順序を保持したまま一つに結合されます。
