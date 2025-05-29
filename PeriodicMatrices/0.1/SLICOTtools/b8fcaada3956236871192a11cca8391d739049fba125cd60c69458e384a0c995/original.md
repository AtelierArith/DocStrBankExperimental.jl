```
 mb03vy!(n::Integer, p::Integer, ilo::Integer, ihi::Integer, A::Array{Float64, 3}, tau::AbstractMatrix{Float64}) -> info::Int64
```

Generate the real orthogonal matrices `Q_1`, `Q_2`, ..., `Q_p`, which are defined as the product of `ihi-ilo` elementary reflectors of order `n`, as returned in `A_1`, `A_2`, ..., `A_p` by `mb03vd!`:

```
 Q_j = H_j(ilo) H_j(ilo+1) . . . H_j(ihi-1).
```

The 3-dimensional arrays `A` and `tau` contains the information on the employed elementary reflectors. The resulting `Q_1`, `Q_2`, ..., `Q_p` overwrite `A_1`, `A_2`, ..., `A_p`. 

See the SLICOT documentation of `MB03VY` for details.
