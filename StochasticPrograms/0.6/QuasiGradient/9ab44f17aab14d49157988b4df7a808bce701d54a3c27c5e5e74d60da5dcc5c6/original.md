```
Termination
```

An optimizer attribute for specifying a termination criterion to be used in the quasi-gradient algorithm. Options are:

  * [`AfterMaximumIterations`](@ref):  Terminate after set number of iterations ?MaximumIterations for parameter descriptions (default)
  * [`AtObjectiveThreshold`](@ref):  Terminate after reaching reference objective ?ObjectiveThreshold for parameter descriptions.
  * [`AtGradientThreshold`](@ref):  Terminate after reaching zero gradient ?GradientThreshold for parameter descriptions.
