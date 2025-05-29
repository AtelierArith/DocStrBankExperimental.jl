```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.ImaginaryTimeGrid,
    c_cdag_index_pairs::Vector{Tuple{Vector{Union{Int64, String}}, Vector{Union{Int64, String}}}};
    gf_filler
) -> Vector{Keldysh.ImaginaryTimeGF{ComplexF64, true}}

```

Compute multiple single-particle Keldysh Green's functions

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

on the imaginary time segment $[0;-i\beta]$ for given compound indices of creation/annihilation operators $i$ and $j$.

## Arguments

  * `ed`:                 Exact Diagonalization object.
  * `grid`:               Time grid on the imaginary time segment.
  * `c_cdag_index_pairs`: List of compound index pairs $(i, j)$.
  * `gf_filler`:          [`Algorithm selector`](@ref AbstractGFFiller) for GF computation.
