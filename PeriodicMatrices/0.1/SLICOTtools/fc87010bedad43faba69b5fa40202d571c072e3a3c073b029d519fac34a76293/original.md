```
mb03wd!(job::AbstractChar, compz::AbstractChar, n::Integer, p::Integer, 
        ilo::Integer, ihi::Integer, iloz::Integer, ihiz::Integer,  h::Array{Float64, 3}, z::Array{Float64, 3}, 
        wr::AbstractVector{Float64}, wi::AbstractVector{Float64}, ldwork::Integer) -> info::Int64
```

Compute the Schur decomposition and the eigenvalues of a product of matrices, H = `H_1`*`H_2`*...*`H_p`, with `H_1` an upper Hessenberg matrix and `H_2`, ..., `H_p` upper triangular matrices, without evaluating the product. Specifically, the matrices Z_i are computed, such that

```
    `Z_1' * H_1 * Z_2 = T_1,`
    `Z_2' * H_2 * Z_3 = T_2,`
           `...`
    `Z_p' * H_p * Z_1 = T_p,`
```

where `T_1` is in real Schur form, and `T_2`, ..., `T_p` are upper triangular.

The routine works primarily with the Hessenberg and triangular submatrices in rows and columns ILO to IHI, but optionally applies the transformations to all the rows and columns of the matrices H_i, i = 1,...,p. The transformations can be optionally accumulated.

See the SLICOT documentation of `MB03WD` for details.
