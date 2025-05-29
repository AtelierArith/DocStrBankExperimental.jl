```
distmesh
3D Mesh Generator using Signed Distance Functions.
Arguments:
    fdist:       Distance function
    fh:          Edge length function
    h:           Smallest edge length

Returns:
    p:           Node positions
    t:           Triangle indices


Example: Unit ball
    d(p) = sqrt(sum(p.^2))-1
    p,t = distmeshnd(d,huniform,0.2)
```
