Brody <: Model 

`Brody` is a concrete type used to represent the Brody model. 

## Description

This model interpolates between the [`Poisson`](@ref) ($\beta=0$) and Wigner-Dyson ($\beta=1$) distributions.  It is commonly used to describe systems with some degree of localization. 

## Attributes

  * `beta`: The level repulsion exponent.

## API

The following spectral statistcs can be evaluated for this model:

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
