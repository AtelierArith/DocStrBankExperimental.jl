```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

[`InverseProductRetraction`](@ref)を返します。これは、2つ以上の[`AbstractInverseRetractionMethod`](@ref)に対して、いずれかが[`InverseProductRetraction`](@ref)自体である場合、他方は（`r`が積の場合は）前に追加されるか、（`s`が積の場合は）後に追加されます。両方が[`InverseProductRetraction`](@ref)である場合、それらは順序を保持して1つに結合されます。
