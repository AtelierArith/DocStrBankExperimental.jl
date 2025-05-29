Poisson <: Model 

`Poisson` is a concrete type used to represent the Poisson model. 

## Description

The Poisson model applies to sequences of independent random variables.  Based on the Berry-Tabor conjecture the spectral statistics (in the semiclassical limit)  of integrable systems are described by this model.

## Attributes

This model has no attributes.

## API

The following spectral statistcs can be evaluated for this model:

  * [`level_spacing_pdf`](@ref)
  * [`level_spacing_cdf`](@ref)
  * [`level_spacing_u`](@ref)
  * [`number_variance`](@ref)
  * [`rigidity`](@ref)
  * [`spectral_form_factor`](@ref)
