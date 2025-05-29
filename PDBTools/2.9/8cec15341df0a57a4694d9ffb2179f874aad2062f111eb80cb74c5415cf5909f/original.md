```
eachsegment(atoms::AbstractVector{<:Atom})
```

Iterator for the segments of a selection.

### Example

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> sit = eachsegment(ats)
 Segment iterator with length = 2

julia> for seg in sit
           @show length(seg)
       end
length(seg) = 1905
length(seg) = 92

julia> collect(sit)
2-element Vector{Segment}[ 
    A-(1905 atoms))
    B-(92 atoms))
]
```
