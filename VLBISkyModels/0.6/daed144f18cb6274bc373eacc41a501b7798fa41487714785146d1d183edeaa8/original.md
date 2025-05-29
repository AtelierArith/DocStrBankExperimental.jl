```julia
struct RingTemplate{R<:VLBISkyModels.AbstractRadial, A<:VLBISkyModels.AbstractAzimuthal} <: VLBISkyModels.AbstractImageTemplate
```

A flexible ring template that forms a ring by taking the product of a radial and azimuthal brightness profile.

A list of radial profiles is given by `subtypes(AbstractRadial)`

A list of azimuthal profiles is given by `subtypes(AbstractAzimuthal)`

## Examples

```julia-repl
julia> rad = RadialGaussian(0.1)
julia> azi = AzimuthalUniform()
julia> ring = modify(RingTemplate(rad, azi), Stretch(10.0), Shift(1.0, 2.0))
```

## Fields

  * `radial`: Radial profile of the ring

  * `azimuthal`: Azimuthal profile of the ring
