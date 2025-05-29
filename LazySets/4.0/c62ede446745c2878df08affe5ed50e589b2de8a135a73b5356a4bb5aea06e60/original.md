```
addconstraint!(P::AbstractPolyhedron, constraint::HalfSpace)
```

Add a linear constraint to a set in constraint representation in-place.

### Input

  * `P`          – set in constraint representation
  * `constraint` – linear constraint to add

### Notes

It is left to the user to guarantee that the dimension of all linear constraints is the same.
