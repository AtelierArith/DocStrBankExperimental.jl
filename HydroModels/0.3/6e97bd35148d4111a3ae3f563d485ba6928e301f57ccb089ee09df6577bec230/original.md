```
HydroFlux{N} <: AbstractHydroFlux
```

Represents a simple flux component with mathematical formulas in a hydrological model. 

# Arguments

  * `inputs::Vector{Num}`: Vector of input variables
  * `outputs::Vector{Num}`: Vector of output variables
  * `params::Vector{Num}=Num[]`: Vector of parameter variables
  * `exprs::Vector{Num}`: Vector of expressions for output calculations
  * `name::Union{Symbol,Nothing}=nothing`: Optional flux identifier

# Fields

  * `exprs::Vector{Num}`: Vector of mathematical expressions
  * `func::Function`: Generated function for flux calculations
  * `infos::NamedTuple`: Metadata (inputs::Vector{Num}, outputs::Vector{Num}, params::Vector{Num})

## Model Structure

The flux model consists of:

  * Input variables: External variables used in calculations
  * Output variables: Computed flux results
  * Parameters: Model parameters used in calculations
  * Expressions: Mathematical formulas defining the relationships

## Metadata Components

The `infos` field tracks:

  * `inputs`: Input variable names
  * `outputs`: Output variable names
  * `params`: Parameter names
