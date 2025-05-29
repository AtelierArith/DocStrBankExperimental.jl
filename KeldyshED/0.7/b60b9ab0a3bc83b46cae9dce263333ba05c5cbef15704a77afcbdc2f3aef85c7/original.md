```julia
computegf(
    ed::KeldyshED.EDCore,
    t1::Keldysh.BranchPoint,
    t2::Keldysh.BranchPoint,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}},
    β::Float64
) -> ComplexF64

```

Compute single-particle Keldysh Green's function

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

at given contour times $t_1$, $t_2$ for given compound indices of creation/annihilation operators $i$ and $j$.

## Arguments

  * `ed`:         Exact Diagonalization object.
  * `t1`:         Contour time $t_1$.
  * `t2`:         Contour time $t_2$.
  * `c_index`:    Compound index $i$.
  * `cdag_index`: Compound index $j$.
  * `β`:          Inverse temperature $\beta$.
