```
mb03vd!(n::Integer, p::Integer, ilo::Integer, ihi::Integer, A::Array{Float64, 3}, tau::AbstractMatrix{Float64}) -> info::Int64
```

Reduce a product of `p` real general matrices `A = A_1*A_2*...*A_p` to upper Hessenberg form, `H = H_1*H_2*...*H_p`, where `H_1` is upper Hessenberg, and `H_2`, ..., `H_p` are upper triangular, by using orthogonal similarity transformations on `A`,

```
    Q_1' * A_1 * Q_2 = H_1,
    Q_2' * A_2 * Q_3 = H_2,
           ...
    Q_p' * A_p * Q_1 = H_p.
```

The matrices `A_1`, `A_2`, ..., `A_p` are contained in the 3-dimensional array `A`.  The resulting `H_1`, `H_2`, ..., `H_p` and `Q_1`, `Q_2`, ..., `Q_p` overwrite  `A_1`, `A_2`, ..., `A_p` in `A` and the array `tau`.   

See the SLICOT documentation of `MB03VD` for details.
