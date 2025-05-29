```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.KeldyshTimeGrid,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}},
    β::Float64;
    gf_filler
) -> Keldysh.TimeInvariantKeldyshTimeGF{ComplexF64, true}

```

Compute single-particle Keldysh Green's function

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)],
\quad \hat\rho = \frac{e^{-\beta\hat H}}{\mathrm{Tr}[e^{-\beta\hat H}]}
$$

on a 2-branch Keldysh contour for given compound indices of creation/annihilation operators $i$ and $j$ with a decoupled initial thermal state at inverse temperature $\beta$.

## Arguments

  * `ed`:         Exact Diagonalization object.
  * `grid`:       Time grid on the 2-branch contour.
  * `c_index`:    Compound index $i$.
  * `cdag_index`: Compound index $j$.
  * `β`:          Inverse temperature $\beta$.
  * `gf_filler`:  [`Algorithm selector`](@ref AbstractGFFiller) for GF computation.
