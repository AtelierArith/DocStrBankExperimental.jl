```julia
computesymbols(identity, ω, θ)
```

Compute or retrieve the symbol matrix for a identity preconditioned operator

# Arguments:

  * `identity::IdentityPC`:  Identity preconditioner to compute symbol matrix for
  * `ω::Array`:              smoothing weighting factor array
  * `θ::Array`:              Fourier mode frequency array (one frequency per dimension)

# Returns:

  * symbol matrix for the identity preconditioner (I)

# Example:

```jldoctest
using LinearAlgebra

# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

# preconditioner
identity = IdentityPC(mass);

# compute symbols
A = computesymbols(identity, [], []);

# verify
@assert A ≈ I

# output

```
