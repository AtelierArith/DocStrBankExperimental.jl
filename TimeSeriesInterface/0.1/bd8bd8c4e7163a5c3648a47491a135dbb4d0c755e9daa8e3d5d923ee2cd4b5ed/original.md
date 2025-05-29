SimulateInput(fit*input::FitInput{T}                 timestamps*forecast::Vector{DateTime}                 exogenous*forecast::Vector{TimeSeries{T}}                 fit*result::FitResult)

SimulateInput is the only information needed by Simulate Functions FitResult may be developed specifically for each FitFunction or you can use the generic version. Ideally all the essential information that flows from fit to simulate should be in the hyperparameters.
