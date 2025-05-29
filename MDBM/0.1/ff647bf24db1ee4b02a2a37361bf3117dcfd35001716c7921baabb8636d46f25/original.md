```
checkneighbour!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}; interpolationorder::Int=0, maxiteration::Int=0)
```

Check the face-neighbouring n-cubes to discover the lost (missing) part of the solutions.

It is possible, that the sub-manifold (e.g.: curve) of the solution is not completely detected (it is interrupted). This way the missing part can be explored similarly to a continuation method (with minimal function evaluation).

It works only if the dimension of the solution object is larger the zero (the maifold is not a set of poins).

```
# Arguments
- `interpolationorder::Int=0`: interpolation order method of the neighbours checked
- `maxiteration::Int=0~: the max number of steps in the 'continuation-like' exploring. If zero, then infinity steps are allowed
```
