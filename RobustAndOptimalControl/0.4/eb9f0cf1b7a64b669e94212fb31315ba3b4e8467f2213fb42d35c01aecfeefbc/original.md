```
se = ExtendedStateSpace(s::AbstractStateSpace; kwargs...)
```

The conversion from a regular statespace object to an `ExtendedStateSpace` creates the following system by default

$$
\begin{bmatrix}
    A & B & B \\
    C & D & D \\
    C & D & D
\end{bmatrix}
$$

i.e., the system and performance mappings are identical, `system_mapping(se) == performance_mapping(se) == s`. However, all matrices `B1, B2, C1, C2; D11, D12, D21, D22` are overridable by a corresponding keyword argument. In this case, the controlled outputs are the same as measured outputs.

Related: `se = convert(ExtendedStateSpace, s::StateSpace)` produces an `ExtendedStateSpace` with empty `performance_mapping` from w->z such that `ss(se) == s`.
