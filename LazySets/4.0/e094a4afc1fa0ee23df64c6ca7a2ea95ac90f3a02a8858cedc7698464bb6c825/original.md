```
isredundant(cmid::HalfSpace, cright::HalfSpace, cleft::HalfSpace)
```

Check whether a linear constraint is redundant wrt. two surrounding constraints.

### Input

  * `cmid`   – linear constraint of concern
  * `cright` – linear constraint to the right (clockwise turn)
  * `cleft`  – linear constraint to the left (counter-clockwise turn)

### Output

`true` iff the constraint is redundant.

### Algorithm

We first check whether the angle between the surrounding constraints is < 180°, which is a necessary condition (unless the direction is identical to one of the other two constraints). If so, we next check if the angle is 0°, in which case the constraint `cmid` is redundant unless it is strictly tighter than the other two constraints. If the angle is strictly between 0° and 180°, the constraint `cmid` is redundant if and only if the vertex defined by the other two constraints lies inside the set defined by `cmid`.
