Defines a Gaussian unitary for an N-mode bosonic system over a 2N-dimensional phase space.

## Fields

  * `basis`: Symplectic basis for Gaussian unitary.
  * `disp`: The displacement vector of length 2N.
  * `symplectic`: The symplectic matrix of size 2N x 2N.
  * `ħ = 2`: Reduced Planck's constant.

## Mathematical description of a Gaussian unitary

An `N`-mode Gaussian unitary, is a unitary operator characterized by a displacement vector `d` of length `2N` and symplectic matrix `S` of size `2N x 2N`, such that its action on a Gaussian state results in a Gaussian state. More specifically, a Gaussian unitary transformation on a Gaussian state is described by its maps on the statistical moments `x̄` and `V` of the Gaussian state: `x̄ → Sx̄ + d` and `V → SVSᵀ`.

## Example

```jldoctest
julia> displace(QuadPairBasis(1), 1.0+im)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
symplectic: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
