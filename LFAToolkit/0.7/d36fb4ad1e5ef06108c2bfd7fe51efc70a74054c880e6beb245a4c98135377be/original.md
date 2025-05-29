```julia
computesymbols(operator, θ)
```

Compute the symbol matrix for an operator

# Arguments:

  * `operator::Operator`:  finite element operator to compute symbol matrix for
  * `θ::Array{Real}`:      Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the operator

# Example:

```jldoctest
using LinearAlgebra;

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

    # compute symbols
    A = computesymbols(diffusion, π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert minimum(eigenvalues) ≈ 1
        @assert maximum(eigenvalues) ≈ 4 / 3
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ 2 / 3
        @assert maximum(eigenvalues) ≈ 64 / 45
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ 1 / 3
        @assert maximum(eigenvalues) ≈ 256 / 225
    end
end

# output

```
