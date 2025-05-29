```
chain_reader(dafs::AbstractVector{<:DafReader}; name::Maybe{AbstractString} = nothing)::DafReader
```

Create a read-only chain wrapper of [`DafReader`](@ref)s, presenting them as a single [`DafReader`](@ref). When accessing the content, the exposed value is that provided by the last data set that contains the data, that is, later data sets can override earlier data sets. However, if an axis exists in more than one data set in the chain, then its entries must be identical. This isn't typically created manually; instead call [`chain_reader`](@ref).

!!! note
    While this verifies the axes are consistent at the time of creating the chain, it's no defense against modifying the chained data after the fact, creating inconsistent axes. *Don't do that*.

