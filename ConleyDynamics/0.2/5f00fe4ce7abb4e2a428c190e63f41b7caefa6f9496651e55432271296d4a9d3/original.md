```
create_lefschetz_gf2(defcellbnd)
```

Create a Lefschetz complex over `GF(2)` by specifying its essential cells and boundaries.

The input argument `defcellbnd` has to be a vector of vectors. Each entry `defcellbnd[k]` has to be of one of the following two forms:

  * `[String, Int, String, String, ...]`: The first `String` contains  the label for the cell `k`, followed by its dimension in the second  entry. The remaining entries are for the labels of the cells which  make up the boundary.
  * `[String, Int]`: This shorther form is for cells with empty boundary. The first entry denotes the cell label, and the second its dimension.

The cells of the resulting Lefschetz complex correspond to the union of all occurring labels. Cell labels that only occur in the boundary specification are assumed to have empty boundary, and they do not have to be specified separately in the second form above. However, if their boundary is not empty, they have to be listed via the above first form as well.

# Examples

```jldoctest
julia> defcellbnd = [["A",0], ["a",1,"B","C"], ["b",1,"B","C"]];

julia> push!(defcellbnd, ["c",1,"B","C"]);

julia> push!(defcellbnd, ["alpha",2,"b","c"]);

julia> lc = create_lefschetz_gf2(defcellbnd);

julia> lc.labels
7-element Vector{String}:
 "A"
 "B"
 "C"
 "a"
 "b"
 "c"
 "alpha"

julia> homology(lc)
3-element Vector{Int64}:
 2
 1
 0
```
