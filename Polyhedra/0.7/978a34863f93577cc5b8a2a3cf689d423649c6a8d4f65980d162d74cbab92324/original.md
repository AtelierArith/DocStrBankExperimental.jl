```
vchebyshevcenter(p::VRep[, solver])
```

Return a tuple with the center and radius of the smallest euclidean ball containing the polyhedron `p`. Throws an error if the polyhedron is empty or if the radius is infinite (i.e. `p` is not a polytope, it contains rays).
