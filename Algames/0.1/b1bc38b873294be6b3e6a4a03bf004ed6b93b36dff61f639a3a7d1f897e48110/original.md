```
WallConstraint{P,T}
```

Constraint of the form

```
   NO constraint violation
```

---

```
          p1 * ///
             |////
```

NO constraint  |////        constraint   violation      |–––> v   violation                  |////                  |////               p2 * /// ––––––––––––––––––––- 	   NO constraint violation

$(x - p1)^T v \leq 0$ where $x = [x[x], x[y]]$, $p1 = [x1,y1]$, $p2 = [x2,y2]$ $v = [xv,yv]$. The ordering of p1 and p2 does not matter.

# Constructor:

```julia
WallConstraint(n, x1::SVector{P}, y1::SVector{P}, x2::SVector{P}, y2::SVector{P}, xv::SVector{P}, yv::SVector{P}, x=1, y=2)
```
