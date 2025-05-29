```
const MultilineMPO = Multiline{<:AbstractMPO}
```

Type that represents multiple lines of `MPO` objects.

# Constructors

```
MultilineMPO(mpos::AbstractVector{<:Union{SparseMPO,DenseMPO}})
MultilineMPO(Os::AbstractMatrix{<:MPOTensor})
```

See also: [`Multiline`](@ref), [`AbstractMPO`](@ref)
