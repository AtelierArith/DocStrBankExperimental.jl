```
minor_axis(matrix::AbstractMatrix)::Maybe{Int8}
```

Return the index of the minor axis of a matrix, that is, the axis one should **vary** for an efficient inner loop accessing the matrix elements. If the matrix doesn't support any efficient access axis, returns `nothing`.
