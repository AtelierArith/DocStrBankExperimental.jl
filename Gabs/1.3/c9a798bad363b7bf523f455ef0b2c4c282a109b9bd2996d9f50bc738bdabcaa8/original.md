Defines a Gaussian channel for an N-mode bosonic system over a 2N-dimensional phase space.

## Fields

  * `basis`: Symplectic representation for Gaussian channel.
  * `disp`: The displacement vector of length 2N.
  * `transform`: The transformation matrix of size 2N x 2N.
  * `noise`: The noise matrix of size 2N x 2N.
  * `ħ = 2`: Reduced Planck's constant.

## Mathematical description of a Gaussian channel

An `N`-mode Gaussian channel is an operator characterized by a displacement vector `d` of length `2N`, as well as a transformation matrix `T` and noise matrix `N` of size `2N x 2N`, such that its action on a Gaussian state results in a Gaussian state. More specifically, a Gaussian channel action on a Gaussian state is described by its maps on the statistical moments `x̄` and `V` of the Gaussian state: `x̄ → Tx̄ + d` and `V → TVTᵀ + N`.

## Example

```jldoctest
julia> noise = [1.0 -3.0; 4.0 2.0];

julia> displace(QuadPairBasis(1), 1.0+im, noise)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
transform: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
noise: 2×2 Matrix{Float64}:
 1.0  -3.0
 4.0   2.0
```
