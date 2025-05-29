pointgroup_robust(a1, a2, a3)

Calculate the pointGroup using an epsilon based on input lattice 

The routine works in a similar fashion to the pointGroup_fast routine but finite precision comparisons use an epsilon scaled to the input. The  epsilon is quite large, 10% (may change) of the smallest scale of the  input. With sufficient testing, this routine may become the defacto standard for the Spacey package.

```
 ```juliadoctest
 julia>  u = [1,0,1e-4]; v = [.5,√3/2,-1e-5]; w = [0,1e-4,√(8/3)];
 julia> pointGroup_robust(u,v,w)
 24-element Array{Array{Float64,2},1}:
 [-1.0 0.0 0.0; -1.0 1.0 0.0; 0.0 0.0 -0.9999999999999999]
 ...
 ```
```
