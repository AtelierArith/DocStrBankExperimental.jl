```
run!(fcm::FuzzyCognitiveMap, iterations::Int; tolerance::Float64=1e-6)
```

Run the FCM simulation for a specified number of iterations or until convergence.

# Arguments

  * `fcm::FuzzyCognitiveMap`: The FCM to simulate
  * `iterations::Int`: Maximum number of iterations to run
  * `tolerance::Float64=1e-6`: Convergence threshold for state changes

# Returns

  * Vector{Float16}: The final state of the FCM after simulation

The simulation stops either when the maximum number of iterations is reached or when the change in state (measured by L2 norm) falls below the tolerance.
