```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

[`ProductRetraction`](@ref)を返します。二つ以上の[`AbstractRetractionMethod`](@ref)の場合、もしそのうちの一つが[`ProductRetraction`](@ref)自体であれば、もう一方は（`m`が積の場合は）前に追加されるか、（`n`が積の場合は）後に追加されます。両方が[`ProductRetraction`](@ref)である場合、それらは順序を保持して一つに結合されます。
