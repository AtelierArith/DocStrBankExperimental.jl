```
BerryRobnik <: Model
```

`BerryRobnik` is a concrete type used to represent the Berry-Robnik model (with two components). 

## Description

This model describes the spectral statistics (in the semiclassical limit)  of systems whose classical phase space features both regular and chaotic motion. These systems are commonly refered to as systems with divided phase space or mixed-type systems. The model rests on the argument that in the semiclassical limit the spectrum subspectra belonging to states that describe  belonging to the states to the distinct types of motion (regular and chaotic) will decompose into separate components. The regular part of the spectrum is modeled by [`Poisson`](@ref) statistics and the chaotic part by [`GOE`](@ref) statistics.

## Attributes

  * `rho`: The Liouville measure of the combined regular component.

## API

The following spectral statistcs can be evaluated for this model:

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
  * [`number_variance`](@ref)
