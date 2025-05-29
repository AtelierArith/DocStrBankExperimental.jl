```
LinearTimeInvariantSystem(A, B, C, D, X, U)
```

A linear time-invariant system with state and input constraints of the form

$$
x' = Ax + Bu,\\
y = Cx + Du,
$$

where $x(t) ∈ X$ and $u(t) ∈ U$ for all $t$.

### Input

  * `A` – matrix
  * `B` – matrix
  * `C` – matrix
  * `D` – matrix
  * `X` – state constraints
  * `U` – input constraints

### Output

A system with output such that the system is a constrained linear control continuous system and the output map is a constrained linear control map.
