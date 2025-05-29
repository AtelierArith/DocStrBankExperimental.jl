```
issubgroup(opsᴳ::T, opsᴴ::T′) where T⁽′⁾<:AbstractVector{SymOperation} --> Bool
```

Determine whether the operations in group $H$ are a subgroup of the group $G$ (each with  operations `opsᴳ` and `opsᴴ`, respectively), i.e. whether $H<G$. Specifically, this requires that $G$ and $H$ are both groups and that for every $h∈H$ there exists an element $g∈G$ such that $h=g$.

Returns a Boolean answer (`true` if normal, `false` if not).

## Note

This compares space groups rather than space group types, i.e. the comparison assumes a matching setting choice between $H$ and $G$. To compare space group types with different conventional settings, they must first be transformed to a shared setting.
