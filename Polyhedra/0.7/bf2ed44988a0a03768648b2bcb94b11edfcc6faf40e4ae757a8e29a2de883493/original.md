```
hrep(halfspaces::HalfSpaceIt; d::FullDim)
```

Creates an H-representation for the polyhedron of full dimension `d` equal to the intersection of the halfspaces `halfspaces`.

### Examples

For instance, the polytope

$$
\begin{aligned}
  x_1 + x_2 &\leq 1 \\
  x_1 - x_2 &\leq 0 \\
  x_1 & \geq 0.
\end{aligned}
$$

can be created as follows:

```julia
hrep([HalfSpace([1, 1], 1), HalfSpace([1, -1], 0), HalfSpace([-1, 0], 0)])
```
