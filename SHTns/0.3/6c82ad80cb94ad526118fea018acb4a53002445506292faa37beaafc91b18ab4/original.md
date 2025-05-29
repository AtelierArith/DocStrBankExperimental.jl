```
mutable struct SHTnsCfg{TR<:Union{Real,Complex}, N<:SHTnsNorm, T<:SHTnsType}
```

  * `cfg::Ptr{shtns_info}`
  * `norm::N`
  * `shtype::T`
  * `robert_form::Bool`
  * `nlm::Int`
  * `lmax::Int`
  * `mmax::Int`
  * `mres::Int`
  * `nlat_2::Int`
  * `nlat::Int`
  * `nphi::Int`
  * `nspat::Int`
  * `li::Vector{Int}`
  * `mi::Vector{Int}`
  * `ct::Vector{Float64}`
  * `st::Vector{Float64}`
  * `nlat_padded::Int`
  * `nlm_cplx::Int`
  * `howmany::Int`

Configuration of spherical harmonic transform.
