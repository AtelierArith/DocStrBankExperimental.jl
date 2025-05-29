```
struct OneDGrid{T<:AbstractFloat, A, Tx, Tfft, Trfft, Talias} <: AbstractGrid{T, A, Talias, D}
```

A one-dimensional `grid`.

  * `device::Any`: device which the grid lives on
  * `nx::Int64`: number of points in $x$
  * `nk::Int64`: number of wavenumbers in $x$
  * `nkr::Int64`: number of positive wavenumbers in $x$ (real Fourier transforms)
  * `dx::AbstractFloat`: grid spacing in $x$
  * `Lx::AbstractFloat`: domain extent in $x$
  * `x::Any`: range with $x$-grid-points
  * `k::Any`: array with $x$-wavenumbers
  * `kr::Any`: array with positive $x$-wavenumbers (real Fourier transforms)
  * `invksq::Any`: array with inverse squared $k$-wavenumbers, $1 / k²$
  * `invkrsq::Any`: array with inverse squared $kᵣ$-wavenumbers, $1 / kᵣ²$
  * `fftplan::Any`: the FFT plan for complex-valued fields
  * `rfftplan::Any`: the FFT plan for real-valued fields
  * `aliased_fraction::AbstractFloat`: the fraction of wavenumbers that are aliased (e.g., 1/3 for quadradic nonlinearities)
  * `kalias::Any`: range of the indices of aliased $x$-wavenumbers
  * `kralias::Any`: range of the indices of aliased positive $x$-wavenumbers (real Fourier transforms)
