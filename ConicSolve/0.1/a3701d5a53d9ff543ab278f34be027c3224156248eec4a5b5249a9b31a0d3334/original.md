```
ConeQP(A, G, P, b, c, h, cones)
```

Constructs a new Conic Quadratic Program.

# Parameters:

  * `A`: The block matrix A in the KKT matrix
  * `G`: The block matrix G in the KKT matrix
  * `P`: The block matrix P in the KKT matrix
  * `b`: The vector b corresponding to $Ax = b$
  * `c`: The vector c corresponding to $c^Tx$
  * `h`: The vector h corresponding to $Gx + s = h$
  * `cones`: A vector of cone types
