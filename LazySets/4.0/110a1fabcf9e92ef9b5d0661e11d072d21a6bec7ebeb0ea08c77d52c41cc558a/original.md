# Extended help

```
vertices_list(H::AbstractHyperrectangle; kwargs...)
```

### Notes

Zeros in the radius are correctly handled, i.e., the result does not contain any duplicate vertices.

### Algorithm

First we identify the dimensions where `H` is flat, i.e., its radius is zero. We also compute the number of vertices that we have to create.

Next we create the vertices. We do this by enumerating all vectors `v` of length `n` (the dimension of `H`) with entries `-1`/`0`/`1` and construct the corresponding vertex as follows:

$$
    \text{vertex}(v)(i) = \begin{cases} c(i) + r(i) & v(i) = 1 \\
                                          c(i) & v(i) = 0 \\
                                          c(i) - r(i) & v(i) = -1. \end{cases}
$$

For enumerating the vectors `v`, we modify the current `v` from left to right by changing entries `-1` to `1`, skipping entries `0`, and stopping at the first entry `1` (but changing it to `-1`). This way we only need to change the vertex in those dimensions where `v` has changed, which usually is a smaller number than `n`.
