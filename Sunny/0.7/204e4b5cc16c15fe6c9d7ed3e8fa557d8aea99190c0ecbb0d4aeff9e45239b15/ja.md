```
symmetry_equivalent_bonds(sys::System, bond::Bond)
```

元の（再形成されていない）結晶の[`Bond`](@ref)を与えると、[`System`](@ref)内のすべての対称的に等価な結合を返します。返される各結合は、[`Site`](@ref)sのペアと`offset`として表され、これは[`set_exchange_at!`](@ref)や[`set_pair_coupling_at!`](@ref)への入力として使用できます。逆結合はイテレータに含まれません（重複カウントはありません）。

# 例

```julia
for (site1, site2, offset) in symmetry_equivalent_bonds(sys, bond)
    @assert site1 < site2
    set_exchange_at!(sys, J, site1, site2; offset)
end
```
