```julia
computesymbols(bddc, ω, θ)
```

Compute the symbol matrix for a BDDC preconditioned operator

# Arguments:

  * `bddc::BDDC`:      BDDC preconditioner to compute symbol matrix for
  * `ω::Array{Real}`:  BDDC smoothing parameter
  * `θ::Array{Real}`:  Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the BDDC preconditioned operator

# Lumped BDDC Example:

```jldoctest
using LinearAlgebra;

for dimension = 2:3
    # setup
    mesh = []
    if dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)
    bddc = LumpedBDDC(diffusion)

    # compute symbols
    A = computesymbols(bddc, [0.2], π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 2
        @assert minimum(eigenvalues) ≈ 0.43999999999999995
        @assert maximum(eigenvalues) ≈ 0.8
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.6319999999999972
        @assert maximum(eigenvalues) ≈ 0.8
    end
end

# output

```

# Dirichlet BDDC Example:

```jldoctest
using LinearAlgebra;

for dimension = 2:3
    # setup
    mesh = []
    if dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)
    bddc = DirichletBDDC(diffusion)

    # compute symbols
    A = computesymbols(bddc, [0.2], π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 2
        @assert minimum(eigenvalues) ≈ 0.7999999999999998
        @assert maximum(eigenvalues) ≈ 0.8
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ 0.7801226993865031
        @assert maximum(eigenvalues) ≈ 0.8
    end
end

# output

```
