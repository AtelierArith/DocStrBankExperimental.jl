```
Segment
```

Segment data structure. Segments must be consecutive in the `atoms` vector, and are identified by having the same `segname` and `model` fields.

The Segment structure carries the properties of the segment  it contains, but it does not copy the original vector of atoms, only the segment meta data and the reference to the original vector. Thus, changes in the segment atoms will be reflected in the original vector of atoms.

### Example

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> segments = collect(eachsegment(ats))
2-element Vector{Segment}[
    A-(1905 atoms))
    B-(92 atoms))
]

julia> segname.(segments[1:2])
2-element Vector{InlineStrings.String7}:
 "A"
 "B"

julia> length(segments[2])
92

```
