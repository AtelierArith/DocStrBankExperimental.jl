```
struct Gauss1DFilter <: AbstractRadFIRFilter
```

One dimensional gaussian filter defined as: f(x) = beta * exp(-0.5*(x/sigma)^2) / length

where x is in the interval [-alpha*sigma, alpha*sigma]

Constructors:

  * `Gauss1DFilter(; fields...)`

Fields:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: standard deviation Default: 1.0
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: total length of the filter Default: 100.0
  * `alpha::AbstractFloat`: the amount of standard deviations to cover in the gaussian window Default: 3.0
  * `beta::AbstractFloat`: scaling factor Default: 1.0
