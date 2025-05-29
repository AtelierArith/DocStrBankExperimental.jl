```
icellfound=GFindLocal!(xref,cellfinder,p; icellstart=1,eps=1.0e-14, trybrute=true)
```

Find cell containing point `p`  starting with cell number `icellstart`.

Returns cell number if found, zero otherwise. If `trybrute==true` try [`gFindBruteForce!`](@ref) before giving up. Upon return, xref contains the barycentric coordinates of the point in the sequence  `dim+1, 1...dim`

!!! warning
    Currently implemented for simplex grids only.

