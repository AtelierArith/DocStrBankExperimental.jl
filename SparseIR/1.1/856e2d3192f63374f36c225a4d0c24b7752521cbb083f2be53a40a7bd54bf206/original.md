```
FiniteTempBasisSet
```

Type for holding IR bases and sparse-sampling objects.

An object of this type holds IR bases for fermions and bosons and associated sparse-sampling objects.

# Fields

  * basis_f::FiniteTempBasis: Fermion basis
  * basis_b::FiniteTempBasis: Boson basis
  * tau::Vector{Float64}: Sampling points in the imaginary-time domain
  * wn_f::Vector{Int}: Sampling fermionic frequencies
  * wn_b::Vector{Int}: Sampling bosonic frequencies
  * smpl*tau*f::TauSampling: Sparse sampling for tau & fermion
  * smpl*tau*b::TauSampling: Sparse sampling for tau & boson
  * smpl*wn*f::MatsubaraSampling: Sparse sampling for Matsubara frequency & fermion
  * smpl*wn*b::MatsubaraSampling: Sparse sampling for Matsubara frequency & boson
  * sve_result::Tuple{PiecewiseLegendrePoly,Vector{Float64},PiecewiseLegendrePoly}: Results of SVE

# Getters

  * beta::Float64: Inverse temperature
  * ωmax::Float64: Cut-off frequency
