```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

Return the [`ProductVectorTransport`](@ref) 2つ以上の[`AbstractVectorTransportMethod`](@ref)のために、1つが[`ProductVectorTransport`](@ref)自体である場合、他方は（`r`がプロダクトの場合は）前に追加されるか（`s`の場合は）後に追加されます。両方が[`ProductVectorTransport`](@ref)である場合、それらは順序を保持して1つに結合されます。
