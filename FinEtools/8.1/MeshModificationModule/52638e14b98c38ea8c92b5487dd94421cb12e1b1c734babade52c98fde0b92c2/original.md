```
interior2boundary(interiorconn::Array{IT,2}, extractb::Array{IT,2}) where {IT<:Integer}
```

Extract the boundary connectivity from the connectivity of the interior.

`extractb` = array that defines in which order the bounding faces are traversed. For     example, for tetrahedra this array is     `extractb = [1 3 2; 1 2 4; 2 3 4; 1 4 3]`
