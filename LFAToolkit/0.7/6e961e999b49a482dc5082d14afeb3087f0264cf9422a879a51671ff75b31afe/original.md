```julia
computesymbols(multigrid, p, v, θ)
```

Compute or retrieve the symbol matrix for a Jacobi preconditioned operator

# Arguments:

  * `multigrid::Multigrid`:  multigrid preconditioner to compute symbol matrix for
  * `p::Array{Real}`:        smoothing paramater array
  * `v::Array{Int}`:         pre and post smooths iteration count array, 0 indicates no pre or post smoothing
  * `θ::Array{Real}`:        Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the multigrid preconditioned operator

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
    ctofbasis = TensorH1LagrangeBasis(3, 5, 1, dimension; collocatedquadrature = true)

    # operators
    finediffusion = GalleryOperator("diffusion", 5, 5, mesh)
    coarsediffusion = GalleryOperator("diffusion", 3, 5, mesh)

    # smoother
    jacobi = Jacobi(finediffusion)

    # preconditioner
    multigrid = PMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis])

    # compute symbols
    A = computesymbols(multigrid, [1.0], [1, 1], π * ones(dimension))

    # verify
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert maximum(eigenvalues) ≈ 0.64
    elseif dimension == 2
        @assert maximum(eigenvalues) ≈ 0.9082562365654528
    elseif dimension == 3
        @assert maximum(eigenvalues) ≈ 1.4359882222222669
    end
end

# output

```
