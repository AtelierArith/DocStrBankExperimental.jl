```
choi_matrix( 𝒩 :: Function, dims :: Vector{Int} ) :: Matrix{ComplexF64}
```

Returns the Choi operator of a channel. The Choi matrix is constructed as

$$
        \Lambda^{AB} = \sum_{i,j \in [d_A]} E^A_{i,j} \otimes \mathcal{N}^{A' \to B}(E_{i,j}^{A'}) ,
$$

where $[d_A]$ is the finite alphabet indexing the input space and $E_{i,j}$ is a square matrix of dimension $d_A$ with a $1$ in the $(i,j)$ entry and a $0$ everywhere else. The input $\Lambda$ is the output dimension.

The input function `𝒩` is called as `𝒩(X)` for arbitrary input `X`. Channel functions with multiple parameters can be considered by declaring a function `𝒩_xy(ρ) = 𝒩(ρ,x,y)` for fixed `(x,y)` and then call, `choi(𝒩_xy, dim_in, dim_out)`.
