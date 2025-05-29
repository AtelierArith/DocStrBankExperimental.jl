`compile(model::FlowModel, params::Vector)` lets you initialize a model `model` with a vector of parameters `params`.

Input arguments

  * `model::FlowModel` - a model of which the dimensionality of its layers/flows has been initialized, but its parameters have not been set.
  * `params::Vector`   - a vector of parameters with which the model should be compiled.

Return arguments

  * `::CompiledFlowModel` - a compiled model with set parameters, such that it can be used for processing data.
