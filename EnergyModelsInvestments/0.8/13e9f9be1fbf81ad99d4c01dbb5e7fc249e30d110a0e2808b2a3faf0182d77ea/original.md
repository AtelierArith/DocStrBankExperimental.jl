Main module for `EnergyModelsInvestments`.

This module implements functionalities allowing to run investment analysis for [EnergyModelsX](https://github.com/EnergyModelsX) system optimization models.

`EnergyModelsInvestments` cannot be used as stand-alone model. Instead, it extends existing models and simplifies the incorporation of investment decisions. It can be used to any JuMP model as long as certain functions are declared. One example is given by [`EnergyModelsBase`](https://energymodelsx.github.io/EnergyModelsBase.jl/stable/).
