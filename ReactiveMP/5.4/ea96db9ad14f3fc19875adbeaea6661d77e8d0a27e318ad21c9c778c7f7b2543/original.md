`compile()` compiles a model by setting its parameters. It randomly sets parameter values in the layers and flows such that inference in the model can be obtained.

Input arguments

  * `model::FlowModel` - a model of which the dimensionality of its layers/flows has been initialized, but its parameters have not been set.

Return arguments

  * `::CompiledFlowModel` - a compiled model with set parameters, such that it can be used for processing data.
