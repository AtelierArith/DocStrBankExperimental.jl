```
struct TwoDGrid{T<:AbstractFloat, A, Tx, Tfft, Trfft, Talias, D} <: AbstractGrid{T, Tk, Talias, D}
```

A two-dimensional `grid`.

  * `device::Any`: device which the grid lives on
  * `nx::Int64`: number of points in $x$
  * `ny::Int64`: number of points in $y$
  * `nk::Int64`: number of wavenumbers in $x$
  * `nl::Int64`: number of wavenumbers in $y$
  * `nkr::Int64`: number of positive wavenumers in $x$ (real Fourier transforms)
  * `dx::AbstractFloat`: grid spacing in $x$
  * `dy::AbstractFloat`: grid spacing in $y$
  * `Lx::AbstractFloat`: domain extent in $x$
  * `Ly::AbstractFloat`: domain extent in $y$
  * `x::Any`: range with $x$-grid-points
  * `y::Any`: range with $y$-grid-points
  * `k::Any`: array with $x$-wavenumbers
  * `l::Any`: array with $y$-wavenumbers
  * `kr::Any`: array with positive $x$-wavenumbers (real Fourier transforms)
  * `Ksq::Any`: array with squared total wavenumbers, $k² + l²$
  * `invKsq::Any`: array with inverse squared total wavenumbers, $1 / (k² + l²)$
  * `Krsq::Any`: array with squared total wavenumbers for real Fourier transforms, $kᵣ² + l²$
  * `invKrsq::Any`: array with inverse squared total wavenumbers for real Fourier transforms, $1 / (kᵣ² + l²)$
  * `fftplan::Any`: the FFT plan for complex-valued fields
  * `rfftplan::Any`: the FFT plan for real-valued fields
  * `aliased_fraction::AbstractFloat`: the fraction of wavenumbers that are aliased (e.g., 1/3 for quadradic nonlinearities)
  * `kalias::Any`: range of the indices of aliased $x$-wavenumbers
  * `kralias::Any`: range of the indices of aliased positive $x$-wavenumbers (real Fourier transforms)
  * `lalias::Any`: range of the indices of aliased $y$-wavenumbers
