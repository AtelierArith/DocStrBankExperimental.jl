```
Wall3DConstraint{P,T}
```

Constraint of the form

```
   NO constraint violation
```

---

  * –––– p1 * ///              |////

NO constraint  |////        constraint   violation      |–––> v   violation                  |////                  |//// p3 * –––– p2 * ///

```
             -
         -|  NO cons. viol.
  p3 *c.v.|
 -    |   |               -
```

  * |  cons.|  |           - |  viol. | |       - |         ||   -

p1 * –––– * p2    |  c.v. -    |  -   -|     NO cons. viol. ––––––––––––––––––––- 	   NO constraint violation The points p1, p2, p3 form a parallelepiped in 3D space.

$(x - p1)^T v \leq 0$ where $x = [x[x], x[y], x[z]]$, $p1 = [x1,y1,z1]$, $p2 = [x2,y2,z2]$, $p3 = [x3,y3,z3]$, $v = [xv,yv,zv]$.

# Constructor:

```julia
Wall3DConstraint(n, x1::SVector{P}, y1::SVector{P}, z1::SVector{P}, x2::SVector{P}, y2::SVector{P}, z2::SVector{P},  x3::SVector{P}, y3::SVector{P}, z3::SVector{P}, xv::SVector{P}, yv::SVector{P}, x=1, y=2, z=3)
```
