BerryRobnikBrody <: Model 

`BerryRobnikBrody` is a concrete type used to represent the Berry-Robnik-Brody model. 

## Description

This model is the Berry-Robnik model (see [`BerryRobnik`](@ref)) where instead of the GOE the [`Brody`](@ref) model is used for the chaotic part.    It is commonly used to describe systems with a divided phase space as well as some degree of localization. 

## Attributes

  * `rho`: The Liouville measure of the combined regular component.
  * `beta`: The level repulsion exponent.

## API

The following spectral statistcs can be evaluated for this model:

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
