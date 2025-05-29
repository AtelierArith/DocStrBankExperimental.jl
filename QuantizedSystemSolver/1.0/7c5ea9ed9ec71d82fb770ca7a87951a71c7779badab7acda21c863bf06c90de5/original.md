```
Stats
```

A struct that holds the statistics of a simulation. It has the following fields:

  * `totalSteps::Int`: The total number of simulation steps.
  * `simulStepCount::Int`: The number of simultaneous steps.
  * `evCount::Int`: The number of events.
  * `numStateSteps::Vector{Int}`: A vector holding the number of steps for each state update.
  * `numInputSteps::Vector{Int}`: A vector holding the number of steps for each input update.
