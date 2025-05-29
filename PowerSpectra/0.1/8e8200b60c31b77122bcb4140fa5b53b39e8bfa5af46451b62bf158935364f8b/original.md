```
mcm(spec::Symbol, alm₁::Alm{T}, alm₂::Alm{T}; lmax=nothing)
```

Compute the mode-coupling matrix. See the [Spectral Analysis](@ref) section in the documentation for examples. These are used by applying the  linear solve operator `\` to a `SpectralArray{T,1}`.

Choices for `spec`:

  * `:TT`, identical to `M⁰⁰`
  * `:TE`, identical to `:ET`, `:TB`, `:BT`, `:M⁰²`, `:M²⁰`
  * `:EE_BB`, returns coupling matrix for stacked EE and BB vectors
  * `:EB_BE`, returns coupling matrix for stacked EB and BE vectors
  * `:M⁺⁺`, sub-block of spin-2 mode-coupling matrices
  * `:M⁻⁻`, sub-block of spin-2 mode-coupling matrices

# Arguments:

  * `spec::Symbol`: cross-spectrum of the mode-coupling matrix
  * `alm₁::Alm{T}`: first mask's spherical harmonic coefficients
  * `alm₂::Alm{T}`: second mask's spherical harmonic coefficients

# Keywords

  * `lmin=0`: minimum multiple for mode-coupling matrix
  * `lmax=nothing`: maximum multipole for mode-coupling matrix

# Returns:

  * the mode coupling matrix. for single symbols, this returns a    `SpectralArray{T,2}`. if spec is `:EE_BB` or `:EB_BE`, returns a    `BlockSpectralMatrix{T}` with 2×2 blocks.
