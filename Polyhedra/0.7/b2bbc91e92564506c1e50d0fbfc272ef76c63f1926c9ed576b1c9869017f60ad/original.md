```
convexhull(P1::VRep, P2::VRep)
```

Takes the convex hull of `P1` and `P2` $\{\, \lambda x + (1-\lambda) y : x \in P_1, y \in P_2 \,\}$. It is very efficient between two V-representations or between two polyhedron for which the V-representation has already been computed. However, if `P1` (resp. `P2`) is a polyhedron for which the V-representation has not been computed yet, it will trigger a representation conversion which is costly.

The type of the result will be chosen closer to the type of `P1`. For instance, if `P1` is a polyhedron (resp. V-representation) and `P2` is a V-representation (resp. polyhedron), `convexhull(P1, P2)` will be a polyhedron (resp. V-representation). If `P1` and `P2` are both polyhedra (resp. V-representation), the resulting polyhedron type (resp. V-representation type) will be computed according to the type of `P1`. The coefficient type however, will be promoted as required taking both the coefficient type of `P1` and `P2` into account.
