```julia
computesymbols(jacobi, ω, θ)
```

Compute or retrieve the symbol matrix for a Jacobi preconditioned operator

# Arguments:

  * `jacobi::Jacobi`:   Jacobi preconditioner to compute symbol matrix for
  * `ω::Array{Real}`:   smoothing weighting factor array
  * `θ::Array{Real}`:   Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the Jacobi preconditioned operator

# Example:

```jldoctest
using LinearAlgebra

for dimension = 1:3
    # setup
    mesh = []
    if dimension == 1
        mesh = Mesh1D(1.0)
    elseif dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)

    # preconditioner
    jacobi = Jacobi(diffusion)

    # compute symbols
    A = computesymbols(jacobi, [1.0], π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert maximum(eigenvalues) ≈ 1 / 7
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ -1 / 14
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.33928571428571486
    end
end

# output

```
