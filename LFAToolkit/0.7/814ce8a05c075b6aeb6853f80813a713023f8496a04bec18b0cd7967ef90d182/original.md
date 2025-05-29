```julia
computesymbolsoverrange(
    multigrid,
    p,
    v,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

Compute the eigenvalues and eigenvectors of the symbol matrix for a multigrid preconditioned operator over a range of θ

# Arguments:

  * `multigrid::Multigrid`:  preconditioner to compute symbol matries for
  * `p::Array{Real}`:        smoothing parameter array
  * `v::Array{Int}`:         pre and post smooths iteration count array, 0 indicates no pre or post smoothing
  * `numbersteps1d::Int`:    number of values of θ to sample in each dimension; note: `numbersteps1d`^`dimension` symbol matrices will be computed

# Keyword Arguments:

  * `mass::Union{Operator,Nothing} = nothing`:  mass operator to invert for comparison to analytic solution
  * `θ_min::Real = -π / 2`:                     bottom of range of θ, shifts range to `[θ_min, θ_min + θ_band]`
  * `θ_band::Real = 2π`:                        `θ_max = θ_min + θ_band`

# Returns:

tuple holding

  * values of θ sampled
  * eigenvalues of symbol matrix at θ sampled
  * eigenvectors of symbol matrix at θ sampled

# Example:

```jldoctest
numbersteps1d = 5;

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
    (_, eigenvalues, _) = computesymbolsoverrange(multigrid, [1.0], [1, 1], numbersteps1d)

    # verify
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert maximum(eigenvalues[4, :]) ≈ 0.64
    elseif dimension == 2
        @assert maximum(eigenvalues[19, :]) ≈ 0.9082562365654528
    elseif dimension == 3
        @assert maximum(eigenvalues[94, :]) ≈ 1.4359882222222669
    end
end

# output

```
