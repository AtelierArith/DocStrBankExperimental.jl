```
struct Node
```

A type representing a node in a finite element model.

  * `ID`: Identification tag
  * `x`: $x$-coordinate
  * `y`: $y$-coordinate
  * `z`: $z$-coordinate
  * `u_x`: Is the node restrained against translation along the global $x$-axis?
  * `u_y`: Is the node restrained against translation along the global $y$-axis?
  * `u_z`: Is the node restrained against translation along the global $z$-axis?
  * `θ_x`: Is the node restrained against rotation about the global $x$-axis?
  * `θ_y`: Is the node restrained against rotation about the global $y$-axis?
  * `θ_z`: Is the node restrained against rotation about the global $z$-axis?
  * `state`: Current state
