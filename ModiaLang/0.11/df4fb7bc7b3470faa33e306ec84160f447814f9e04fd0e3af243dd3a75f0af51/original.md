```
simulationModel = SimulationModel{FloatType,TimeType}(
        modelModule, modelName, getDerivatives!, equationInfo, x_startValues,
        parameters, variableNames;
        vSolvedWithInitValuesAndUnit::OrderedDict{String,Any}(),
        vEliminated::Vector{Int}=Int[],
        vProperty::Vector{Int}=Int[],
        var_name::Function = v->nothing)
```

# Arguments

  * `modelModule`: Module in which `@instantiateModel` is invoked (it is used for `Core.eval(modelModule, ...)`), that is evaluation of expressions in the environment of the user.
  * `modelName::String`: Name of the model
  * `getDerivatives::Function`: Function that is used to evaluate the model equations, typically generated with [`ModiaLang.generate_getDerivatives!`].
  * `equationInfo::ModiaBase.EquationInfo`: Information about the states and the equations.
  * `x_startValues`:: Deprecated (is no longer used).
  * `parameters`: A hierarchical NamedTuple of (key, value) pairs defining the parameter and init/start values.
  * variableNames: A vector of variable names. A name can be a Symbol or a String.
