```
normals{VT,FD,FT,FO}(vertices::Vector{Point{3, VT}},
                    faces::Vector{Face{FD,FT,FO}},
                    NT = Normal{3, VT})
```

Compute all vertex normals.
