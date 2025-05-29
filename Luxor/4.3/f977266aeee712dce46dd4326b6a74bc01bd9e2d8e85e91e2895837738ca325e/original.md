```
getrotation(R::Matrix)
getrotation()
```

Get the rotation of a Julia 3x3 matrix, or the current Luxor rotation.

```julia-repl
julia> getrotation()
0.0
```

$$
\begin{bmatrix}
a & b & tx \\
c & d & ty \\
0 & 0 & 1  \\
\end{bmatrix}
$$

The rotation angle is `atan(-b, a)` or `atan(c, d)`.

See `getmatrix()` for details.
