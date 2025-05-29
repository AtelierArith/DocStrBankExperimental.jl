```
MPO(os::OpSum, sites::Vector{<:Index}; splitblocks=true, kwargs...)
MPO(eltype::Type{<:Number}, os::OpSum, sites::Vector{<:Index}; splitblocks=true, kwargs...)
```

Convert an OpSum object `os` to an MPO, with indices given by `sites`. The resulting MPO will have the indices `sites[1], sites[1]', sites[2], sites[2]'` etc. The conversion is done by an algorithm that compresses the MPO resulting from adding the OpSum terms together, often achieving the minimum possible bond dimension.

Optionally specify the desired element type of the output MPO by passing the type as the first argument.

The keyword argument `splitblocks` controls the sparsity of the resulting MPO. With the default `splitblocks=true`, the link indices of the MPO are split into blocks of dimension 1, potentially making the MPO more sparse.

With the `splitblocks=false`, the blocks of the link dimensions are packed as much as possible according to common quantum numbers, making larger blocks. Before ITensors 0.3.19, this was the default output, but we have found that in general MPOs output with `splitblocks=true` lead to better performance in algorithms like DMRG.

# Examples

```julia
os = OpSum()
os += "Sz",1,"Sz",2
os += "Sz",2,"Sz",3
os += "Sz",3,"Sz",4

sites = siteinds("S=1/2",4)
H = MPO(os,sites)
H = MPO(Float32,os,sites)
H = MPO(os,sites; splitblocks=false)
```
