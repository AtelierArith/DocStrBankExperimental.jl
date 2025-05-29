```
struct ThreeDGrid{T<:AbstractFloat, Tk, Tx, Tfft, Trfft, Talias} <: AbstractGrid{T, Tk, Talias}
```

A three-dimensional `grid`.

  * `device::Any`: device which the grid lives on
  * `nx::Int64`: number of points in $x$
  * `ny::Int64`: number of points in $y$
  * `nz::Int64`: number of points in $z$
  * `nk::Int64`: number of wavenumbers in $x$
  * `nl::Int64`: number of wavenumbers in $y$
  * `nm::Int64`: number of wavenumbers in $z$
  * `nkr::Int64`: number of positive wavenumers in $x$ (real Fourier transforms)
  * `dx::AbstractFloat`: grid spacing in $x$
  * `dy::AbstractFloat`: grid spacing in $y$
  * `dz::AbstractFloat`: grid spacing in $z$
  * `Lx::AbstractFloat`: domain extent in $x$
  * `Ly::AbstractFloat`: domain extent in $y$
  * `Lz::AbstractFloat`: domain extent in $z$
  * `x::Any`: range with $x$-grid-points
  * `y::Any`: range with $y$-grid-points
  * `z::Any`: range with $z$-grid-points
  * `k::Any`: array with $x$-wavenumbers
  * `l::Any`: array with $y$-wavenumbers
  * `m::Any`: array with $z$-wavenumbers
  * `kr::Any`: array with positive $x$-wavenumbers (real Fourier transforms)
  * `Ksq::Any`: array with squared total wavenumbers, $k² + l² + m²$
  * `invKsq::Any`: array with inverse squared total wavenumbers, $1 / (k² + l² + m²)$
  * `Krsq::Any`: array with squared total wavenumbers for real Fourier transforms, $kᵣ² + l² + m²$
  * `invKrsq::Any`: array with inverse squared total wavenumbers for real Fourier transforms, $1 / (kᵣ² + l² + m²)$
  * `fftplan::Any`: the FFT plan for complex-valued fields
  * `rfftplan::Any`: the FFT plan for real-valued fields
  * `aliased_fraction::AbstractFloat`: the fraction of wavenumbers that are aliased (e.g., 1/3 for quadradic nonlinearities)
  * `kalias::Any`: range of the indices of aliased $x$-wavenumbers
  * `kralias::Any`: range of the indices of aliased positive $x$-wavenumbers (real Fourier transforms)
  * `lalias::Any`: range of the indices of aliased $y$-wavenumbers
  * `malias::Any`: range of the indices of aliased $m$-wavenumbers
