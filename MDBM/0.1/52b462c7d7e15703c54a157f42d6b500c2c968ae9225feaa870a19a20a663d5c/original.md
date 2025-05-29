```
refine!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}; directions::Vector{T}=collect(Int64,1:N)) where N where Nf where Nc where T<:Integer
```

Double the resolution of the axes along the provided `directions` then halving the `ncubes` accordingly.

# Examples

```jldoctest
julia> refine!(mymdbm)
julia> refine!(mymdbm,[1,1,2])
```
