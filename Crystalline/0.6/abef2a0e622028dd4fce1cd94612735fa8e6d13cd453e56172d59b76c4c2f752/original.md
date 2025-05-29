```
isnormal(opsᴳ::AbstractVector{<:SymOperation},
         opsᴴ::AbstractVector{<:SymOperation};
         verbose::Bool=false)                    --> Bool
```

Determine whether the operations in group $H$ are normal in the group $G$ (each with  operations `opsᴳ` and `opsᴴ`), in the sense that 

$$
ghg⁻¹ ∈ H, ∀ g∈G, ∀ h∈H
$$

Returns a Boolean answer (`true` if normal, `false` if not).

## Note

This compares space groups rather than space group types, i.e. the comparison assumes a matching setting choice between $H$ and $G$. To compare space group types with different conventional settings, they must first be transformed to a shared setting.
