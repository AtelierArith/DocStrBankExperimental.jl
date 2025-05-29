```julia
computesymbols(chebyshev, ω, θ)
```

Compute or retrieve the symbol matrix for a Chebyshev preconditioned operator

# Arguments:

  * `chebyshev::Chebyshev`:  Chebyshev preconditioner to compute symbol matrix for
  * `ω::Array{Real}`:        smoothing parameter array [degree], [degree, $\lambda_{\text{max}}$], or [degree, $\lambda_{\text{min}}$, $\lambda_{\text{max}}$]
  * `θ::Array{Real}`:        Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the Chebyshev preconditioned operator

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
    chebyshev = Chebyshev(diffusion)

    # compute symbols
    A = computesymbols(chebyshev, [1], π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert minimum(eigenvalues) ≈ 0.15151515151515105
        @assert maximum(eigenvalues) ≈ 0.27272727272727226
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ -0.25495098334134725
        @assert maximum(eigenvalues) ≈ -0.17128758445192374
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.8181818181818181
        @assert maximum(eigenvalues) ≈ -0.357575757575757
    end
end

# output

```
