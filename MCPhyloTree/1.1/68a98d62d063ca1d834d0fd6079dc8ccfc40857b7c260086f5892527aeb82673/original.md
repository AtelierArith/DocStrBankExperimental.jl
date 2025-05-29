```
from_leave_incidence_matrix(lm::A, names) where A<:AbstractArray{<:Real, 2}
```

Build the tree which is specified through a leave incidence matrix. The function $leave_incidence_matrix$ from this package creates such a matrix.

Returns the root node of the tree build from the matrix.

  * `lm` : leave incidence matrix
  * `names` : list of names for the leaves (in order of the rows)
