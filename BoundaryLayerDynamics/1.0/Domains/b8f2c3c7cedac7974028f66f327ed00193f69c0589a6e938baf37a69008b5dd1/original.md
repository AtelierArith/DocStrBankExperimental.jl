```
CustomBoundary(; boundary_behaviors...)
```

A boundary that explicitly specifies the mathematical boundary conditions for all state variables. Boundary conditions can be specified as keyword arguments, where the key is the name of the field and the value is either one of `:dirichlet` or `:neumann` for homogeneous boundary conditions, or a `Pair` that includes the non-zero value, such as `:dirichlet => 1`.

# Example

```
CustomBoundary(vel1 = :dirichlet => 1, vel2 = :dirichlet, vel3 = :neumann)
```
