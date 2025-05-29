```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.ImaginaryTimeGrid,
    c_index::Vector{Union{Int64, String}},
    cdag_index::Vector{Union{Int64, String}};
    gf_filler
) -> Keldysh.ImaginaryTimeGF{ComplexF64, true}

```

Compute single-particle Keldysh Green's function

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

on the imaginary time segment $[0;-i\beta]$ for given compound indices of creation/annihilation operators $i$ and $j$.

## Arguments

  * `ed`:         Exact Diagonalization object.
  * `grid`:       Time grid on the imaginary time segment.
  * `c_index`:    Compound index $i$.
  * `cdag_index`: Compound index $j$.
  * `gf_filler`:  [`Algorithm selector`](@ref AbstractGFFiller) for GF computation.
