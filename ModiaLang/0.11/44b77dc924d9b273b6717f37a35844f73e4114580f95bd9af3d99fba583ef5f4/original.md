```
modelInstance = @instantiateModel(model; FloatType = Float64, aliasReduction=true, unitless=false,
    evaluateParameters=false, log=false, logModel=false, logDetails=false, logStateSelection=false,
    logCode=false,logExecution=logExecution, logCalculations=logCalculations, logTiming=false)
```

Instantiates a model, i.e. performs structural and symbolic transformations and generates a function for calculation of derivatives suitable for simulation.

  * `model`: model (declarations and equations)
  * `FloatType`: Variable type for floating point numbers, for example: Float64, Measurements{Float64}, StaticParticles{Float64,100}, Particles{Float64,2000}
  * `aliasReduction`: Perform alias elimination and remove singularities
  * `unitless`: Remove units (useful while debugging models and needed for MonteCarloMeasurements)
  * `evaluateParameters`: Use evaluated parameters in the generated code.
  * `log`: Log the different phases of translation
  * `logModel`: Log the variables and equations of the model
  * `logDetails`: Log internal data during the different phases of translation
  * `logStateSelection`: Log details during state selection
  * `logCode`: Log the generated code
  * `logExecution`: Log the execution of the generated code (useful for timing compilation)
  * `logCalculations`: Log the calculations of the generated code (useful for finding unit bugs)
  * `logTiming`: Log timing of different phases
  * `return modelInstance prepared for simulation`
