```julia
computegf(
    ed::KeldyshED.EDCore,
    grid::Keldysh.FullTimeGrid,
    c_indices::Vector{Vector{Union{Int64, String}}},
    cdag_indices::Vector{Vector{Union{Int64, String}}};
    gf_filler
) -> Keldysh.TimeInvariantFullTimeGF{ComplexF64, false}

```

Compute a matrix-valued single-particle Keldysh Green's function

$$
G_{ij}(t_1, t_2) =
-i \mathrm{Tr}[\hat\rho \mathbb{T}_\mathcal{C} c_i(t_1) c^\dagger_j(t_2)]
$$

on a 3-branch Konstantinov-Perel' contour for all possible pairs of compound indices $(i, j)$ given a list of $i$ and a list of $j$ (the lists must have equal length).

## Arguments

  * `ed`:           Exact Diagonalization object.
  * `grid`:         Time grid on the 3-branch contour.
  * `c_indices`:    List of compound indices $i$.
  * `cdag_indices`: List of compound indices $j$.
  * `gf_filler`:    [`Algorithm selector`](@ref AbstractGFFiller) for GF computation.
