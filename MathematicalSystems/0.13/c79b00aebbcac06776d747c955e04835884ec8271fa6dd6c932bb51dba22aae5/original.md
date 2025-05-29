```
islinear(s::AbstractSystem)
```

Determines whether the dynamics of system `s` is specified by linear equations.

### Notes

We adopt the notion from [Section 2.7, 1]. For example, the system with inputs $x' = f(t, x, u) = A x + B u$ is linear, since the function $f(t, ⋅, ⋅)$ is linear in $(x, u)$ for each $t ∈ \mathbb{R}$. On the other hand, $x' = f(t, x, u) = A x + B u + c$ is affine but not linear, since it is not linear in $(x, u)$.

The result of this function only depends on the system type, not the value, and can also be applied to `typeof(s)`. So, if a system type allows an instance that is not linear, it returns `false` by default. For example, polynomial systems can be nonlinear; hence `islinear` returns `false`.

[1] Sontag, Eduardo D. *Mathematical control theory: deterministic finite dimensional systems.* Vol. 6. Springer Science & Business Media, 2013.
