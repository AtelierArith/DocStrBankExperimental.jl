This package exports

  * `BOpt`, `boptimize!`
  * acquisition types: `ExpectedImprovement`, `ProbabilityOfImprovement`, `UpperConfidenceBound`, `ThompsonSamplingSimple`, `MutualInformation`
  * scaling of standard deviation in `UpperConfidenceBound`: `BrochuBetaScaling`, `NoBetaScaling`
  * GP hyperparameter optimizer: `MAPGPOptimizer`, `NoModelOptimizer`
  * Initializer: `ScaledSobolIterator`, `ScaledLHSIterator`
  * optimization sense: `Min`, `Max`
  * verbosity levels: `Silent`, `Timings`, `Progress`
  * helper: maxduration!, maxiterations!

Use the REPL help, e.g. `?Bopt`, to get more information.
