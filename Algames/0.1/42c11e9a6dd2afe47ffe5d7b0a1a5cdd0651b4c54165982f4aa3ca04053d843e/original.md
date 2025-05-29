```
CylinderConstraint{P,T}
```

Constraint of the form

```
   NO constraint violation
```

---

```
			NO constraint
			violation
			       r
                 ---->
             ////|////  ^
             ////|////  |
```

NO constraint  /// v ///  |     NO constraint   violation      ////^////  |l    violation                  ////|con.  |                  ////|vio.  |                  / p * ///  |

---

```
   NO constraint violation
```

The p is the origin, v is the direction, l is the length, r is the radius

# Constructor:

```julia
CylinderConstraint(n, p1::SVector{P}, p2::SVector{P}, p3::SVector{P},
	v::SVector{P},  l::SVector{P}, r::SVector{P}, x=1, y=2, z=3)
```
