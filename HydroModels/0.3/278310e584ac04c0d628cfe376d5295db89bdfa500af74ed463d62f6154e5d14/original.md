```
StateFlux{N} <: AbstractStateFlux
```

Represents a state flux component in a hydrological model that describes how state variables  change over time. The type parameter `N` is used to encode the component name at the type  level for better type stability.

# Arguments

  * `inputs::Vector{Num}`: Vector of input variables affecting state change
  * `state::Num`: State variable being updated
  * `params::Vector{Num}=Num[]`: Optional vector of parameter variables
  * `expr::Num`: Expression defining the state derivative
  * `name::Union{Symbol,Nothing}=nothing`: Optional flux identifier

# Fields

  * `exprs::Vector{Num}`: Vector of state derivative expressions
  * `infos::NamedTuple`: Component metadata including input, state, and parameter information

# Description

StateFlux is a type-stable implementation for representing state changes in hydrological models. It defines how state variables evolve over time based on inputs, current state, and parameters. The component can be constructed in three ways to accommodate different modeling needs:

## Model Structure

The state flux model consists of:

  * Input variables: External variables affecting state change
  * State variable: The variable being updated
  * Parameters: Model parameters used in calculations
  * Expression: Mathematical formula defining state derivative

## Metadata Components

The `infos` field tracks:

  * `inputs`: Input variable names
  * `states`: State variable names
  * `params`: Parameter names
  * `inflows`: Input flux names (when constructed from fluxes)
  * `outflows`: Output flux names (when constructed from fluxes)

## Construction Methods

1. Explicit Definition:

    ```julia
    # Define state change as a function of inputs and parameters
    flux = StateFlux(
        inputs=[precip, evap],  # input variables
        state=soil_moisture,    # state variable
        params=[k₁, k₂],       # parameters
        expr=k₁*precip - k₂*evap  # state derivative
    )
    ```
2. Flux-Based Definition:

    ```julia
    # Define state change as difference between inflows and outflows
    flux = StateFlux(
        [inflow₁, inflow₂] => [outflow₁, outflow₂],  # input/output fluxes
        soil_moisture                                  # state variable
    )
    ```
3. State Transition:

    ```julia
    # Define direct state transition
    flux = StateFlux(
        old_state => new_state  # state transition pair
    )
    ```

## Usage Notes

1. State derivatives are automatically calculated from expressions
2. Names are auto-generated from state variables if not provided
3. StateFlux components must be used within a HydroBucket
4. Flux pairs automatically create mass-balance equations
