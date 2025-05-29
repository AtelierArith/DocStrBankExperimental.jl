```
ProductSector{T<:SectorTuple}
```

Represents the Deligne tensor product of sectors. The type parameter `T` is a tuple of the component sectors. The recommended way to construct a `ProductSector` is using the [`deligneproduct`](@ref) (`⊠`) operator on the components.
