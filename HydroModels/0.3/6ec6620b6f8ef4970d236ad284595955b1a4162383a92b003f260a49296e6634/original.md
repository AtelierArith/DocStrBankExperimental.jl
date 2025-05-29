```
NeuralFlux{N} <: AbstractNeuralFlux
```

Represents a neural network-based flux component in a hydrological model. The type parameter  `N` is used to encode the component name at the type level for better type stability.

# Arguments

  * `inputs::Vector{Num}`: Vector of input variables
  * `outputs::Vector{Num}`: Vector of output variables
  * `chain::LuxCore.AbstractLuxLayer`: Neural network model
  * `name::Union{Symbol,Nothing}=nothing`: Optional flux identifier
  * `chain_name::Union{Symbol,Nothing}=nothing`: Optional neural network identifier

# Fields

  * `chain::LuxCore.AbstractLuxLayer`: Neural network model
  * `func::Function`: Generated function for flux calculations
  * `infos::NamedTuple`: Component metadata

# Model Structure

The neural flux model consists of:

  * Input variables: External variables fed to neural network
  * Output variables: Neural network predictions
  * Neural network: Machine learning model
  * Generated function: Optimized implementation for calculations

## Metadata Components

The `infos` field tracks:

  * `inputs`: Input variable names
  * `outputs`: Output variable names
  * `nns`: Neural network names
  * `nn_inputs`: Neural network input names
  * `nn_outputs`: Neural network output names
