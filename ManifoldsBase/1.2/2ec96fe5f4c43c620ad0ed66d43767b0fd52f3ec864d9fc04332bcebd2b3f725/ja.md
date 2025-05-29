```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

Return the [`ProductVectorTransport`](@ref) 2つ以上の[`AbstractVectorTransportMethod`](@ref)のために、1つが[`ProductVectorTransport`](@ref)自体である場合、他方は前に追加される（`r`がプロダクトの場合）か、後に追加される（`s`の場合）ことになります。両方が[`ProductVectorTransport`](@ref)である場合、それらは順序を保持して1つに結合されます。
