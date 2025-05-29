```julia
computesymbolsoverrange(
    operator,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

Compute the eigenvalues and eigenvectors of the symbol matrix for an operator over a range of θ

# Arguments:

  * `operator::Operator`:  finite element operator to compute symbol matrices for
  * `numbersteps1d::Int`:  number of values of θ to sample in each dimension; note: `numbersteps1d`^`dimension` symbol matrices will be computed

# Keyword Arguments:

  * `mass::Union{Operator,Nothing} = nothing`:  mass operator to invert for comparison to analytic solution
  * `θ_min::Real = -π / 2`:                     bottom of range of θ, shifts range to `[θ_min, θ_min + θ_band]`
  * `θ_band::Real = 2π`:                        `θ_max = θ_min + θ_band`

# Returns:

tuple holding

  * values of θ sampled
  * eigenvalues of symbol matrix at θ sampled
  * eigenvectors of symbol matrix at θ sampled

# Examples:

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

    # compute symbols
    (_, eigenvalues, _) = computesymbolsoverrange(diffusion, numbersteps1d)

    # verify
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert minimum(eigenvalues[4, :]) ≈ 1
        @assert maximum(eigenvalues[4, :]) ≈ 4 / 3
    elseif dimension == 2
        @assert minimum(eigenvalues[19, :]) ≈ 2 / 3
        @assert maximum(eigenvalues[19, :]) ≈ 64 / 45
    elseif dimension == 3
        @assert minimum(eigenvalues[94, :]) ≈ 1 / 3
        @assert maximum(eigenvalues[94, :]) ≈ 256 / 225
    end
end

# output

```

```jldoctest
# setup
numbersteps1d = 3;
mesh = Mesh2D(0.5, 0.5);
p = 6;

# operators
mass = GalleryOperator("mass", p + 1, p + 1, mesh);
diffusion = GalleryOperator("diffusion", p + 1, p + 1, mesh);

# compute symbols
(_, eigenvalues, _) =
    computesymbolsoverrange(diffusion, numbersteps1d; mass = mass, θ_min = -π);
eigenvalues = real(eigenvalues);

@assert minimum(eigenvalues[2, :]) ≈ π^2

# output

```
