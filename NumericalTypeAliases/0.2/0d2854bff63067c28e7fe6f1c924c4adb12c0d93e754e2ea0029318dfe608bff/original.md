Main module for `NumericalTypeAliases.jl`, a Julia package of numerical array type aliases.

This module exports all of the type aliases and utilities used by the `NumericalTypeAliases.jl package.`

# Basic Usage

Install and import the package interactively with

```julia-repl
julia> ]
(@v1.9) pkg> add NumericalTypeAliases
```

Then develop your package with numerical aliases such as

```julia
using NumericalTypeAliases

function do_something(data::RealMatrix, labels::IntegerVector)
    # Write a function that requires a 2-D float matrix and integer vector.
end
```

# Imports

The following names are imported by the package as dependencies:

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `Pkg`

# Exports

The following names are exported and available when `using` the package:

  * [`Float`](@ref)
  * [`IntegerArray`](@ref)
  * [`IntegerMatrix`](@ref)
  * [`IntegerVector`](@ref)
  * [`NTA_ABSTRACT_TYPES`](@ref)
  * [`NTA_CONCRETE_TYPES`](@ref)
  * [`NTA_TYPES`](@ref)
  * [`NTA_VERSION`](@ref)
  * [`RealArray`](@ref)
  * [`RealFP`](@ref)
  * [`RealMatrix`](@ref)
  * [`RealVector`](@ref)
