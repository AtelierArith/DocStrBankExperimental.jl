```
generaldyne(state::GaussianState, indices::Vector; proj = (ħ/2)I) -> Generaldyne
generaldyne(state::GaussianState, index::Int; proj = (ħ/2)I) -> Generaldyne
```

Compute the projection of the subsystem of a Gaussian state `state` indicated by `indices` on `proj` and return a `Generaldyne` object. The keyword argument `proj` can take the following forms:

  * If `proj` is a matrix, then the subsystem is projected onto a Gaussian state with a randomly sampled mean and covariance matrix `result`.
  * If `proj` is a Gaussian state, then the subsystem is projected onto `proj`.

The `result` and mapped state `output` can be obtained from the Generaldyne object `M` via `M.result` and `M.output`. Iterating the decomposition produces the components `result` and `output`.

Note the measured modes are replaced with vacuum states after the general-dyne measurement.

# Examples

```
julia> st = squeezedstate(QuadBlockBasis(3), 1.0, pi/4);

julia> M = generaldyne(st, [1, 3])
Generaldyne{GaussianState{QuadBlockBasis{Int64}, Vector{Float64}, Matrix{Float64}}, GaussianState{QuadBlockBasis{Int64}, Vector{Float64}, Matrix{Float64}}}
result:
GaussianState for 2 modes.
  symplectic basis: QuadBlockBasis
mean: 4-element Vector{Float64}:
  0.26967410461090285
  1.4683993027500133
 -1.84631450059537
  0.16832788926417352
covariance: 4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0
output state:
GaussianState for 3 modes.
  symplectic basis: QuadBlockBasis
mean: 6-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
covariance: 6×6 Matrix{Float64}:
 1.0   0.0      0.0  0.0   0.0      0.0
 0.0   1.19762  0.0  0.0  -2.56458  0.0
 0.0   0.0      1.0  0.0   0.0      0.0
 0.0   0.0      0.0  1.0   0.0      0.0
 0.0  -2.56458  0.0  0.0   6.32677  0.0
 0.0   0.0      0.0  0.0   0.0      1.0

julia> result, state = M; # destructuring via iteration

julia> result == M.result && state == M.state
true
```
