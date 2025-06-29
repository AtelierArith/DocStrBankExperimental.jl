A mutable struct that represents a model with three components: iceflow, mass balance, and machine learning.

```
Model{IFM <: AbstractEmptyModel, MBM <: AbstractEmptyModel, MLM <: AbstractEmptyModel}
```

# Keyword arguments

  * `iceflow::Union{IFM, Vector{IFM}}`: Represents the iceflow component, which can be a single instance of `IFM` or a vector of `IFM` instances.
  * `mass_balance::Union{MBM, Vector{MBM}}`: Represents the mass balance component, which can be a single instance of `MBM` or a vector of `MBM` instances.
  * `machine_learning::MLM`: Represents the machine learning component, which is an instance of `MLM`.

# Type Parameters

  * `IFM`: A subtype of `AbstractEmptyModel` representing the type of the iceflow model.
  * `MBM`: A subtype of `AbstractEmptyModel` representing the type of the mass balance model.
  * `MLM`: A subtype of `AbstractEmptyModel` representing the type of the machine learning model.
