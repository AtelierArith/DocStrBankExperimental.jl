```
mod(f::T, g::T) where T <: RingElem
```

Return the Euclidean remainder of $f$ by $g$. A `DivideError` should be thrown if $g$ is zero.

!!! note
    For best compatibility with the internal assumptions made by AbstractAlgebra, the Euclidean remainder function should provide unique representatives for the residue classes; the `mod` function should satisfy

    1. `mod(a_1, b) = mod(a_2, b)` if and only if $b$ divides $a_1 - a_2$, and
    2. `mod(0, b) = 0`.

