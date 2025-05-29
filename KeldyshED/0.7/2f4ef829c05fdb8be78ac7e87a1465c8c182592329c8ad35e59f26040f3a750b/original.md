```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.FullTimeGrid,
    c_cdag_index_pairs::Vector{Tuple{Vector{Union{Int64, String}}, Vector{Union{Int64, String}}}};
    gf_filler
) -> Vector{Keldysh.TimeInvariantFullTimeGF{ComplexF64, true}}

```

Compute multiple single-particle Keldysh Green's functions

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

on a 3-branch Konstantinov-Perel' contour for given compound indices of creation/annihilation operators $i$ and $j$.

## Arguments

  * `ed`:                 Exact Diagonalization object.
  * `grid`:               Time grid on the 3-branch contour.
  * `c_cdag_index_pairs`: List of compound index pairs $(i, j)$.
  * `gf_filler`:          [`Algorithm selector`](@ref AbstractGFFiller) for GF computation.
