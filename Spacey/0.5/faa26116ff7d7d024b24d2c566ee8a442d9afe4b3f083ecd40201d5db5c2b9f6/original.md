Generate the symmetry operations of a lattice, defined by three 3-vectors. This function aims to be more efficient than `pointGroup_basic` and so is more complex

```juliadoctest
julia> u = [1,0,0]; v = [.5,√3/2,0]; w = [0,0,√(8/3)];
julia> pointGroup(u,v,w)
24-element Array{Array{Float64,2},1}:
[-1 -1 0; 0 1 0; 0 0 -1]
...
```
