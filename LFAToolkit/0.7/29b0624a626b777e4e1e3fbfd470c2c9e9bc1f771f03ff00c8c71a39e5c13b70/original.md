```julia
computesymbolsoverrange(
    preconditioner,
    ω,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

Compute the eigenvalues and eigenvectors of the symbol matrix for a preconditioned operator over a range of θ

# Arguments:

  * `preconditioner::AbstractPreconditioner`:  preconditioner to compute symbol matries for
  * `ω::Array`:                                smoothing parameter array
  * `numbersteps1d::Int`:                      number of values of θ to sample in each dimension; note: `numbersteps1d`^`dimension` symbol matrices will be computed

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
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)

    # preconditioner
    chebyshev = Chebyshev(diffusion)

    # compute symbols
    (_, eigenvalues, _) = computesymbolsoverrange(chebyshev, [1], numbersteps1d)

    # verify
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert minimum(eigenvalues[4, :]) ≈ 0.15151515151515105
        @assert maximum(eigenvalues[4, :]) ≈ 0.27272727272727226
    elseif dimension == 2
        @assert minimum(eigenvalues[19, :]) ≈ -0.25495098334134725
        @assert maximum(eigenvalues[19, :]) ≈ -0.17128758445192374
    elseif dimension == 3
        @assert minimum(eigenvalues[94, :]) ≈ -0.8181818181818181
        @assert maximum(eigenvalues[94, :]) ≈ -0.357575757575757
    end
end

# output

```
