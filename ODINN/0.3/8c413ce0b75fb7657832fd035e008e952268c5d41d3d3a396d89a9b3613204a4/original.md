```
run!(simulation::FunctionalInversion)
```

Run the training process for a given `FunctionalInversion` simulation.

# Arguments

  * `simulation::FunctionalInversion`: The simulation object containing the parameters and settings for the functional inversion process.

# Description

This function initiates the training of a Universal Differential Equation (UDE) for the provided simulation. It prints a message indicating the start of the training process, calls the `train_UDE!` function to perform the training, and collects the results in `results_list`. The results are intended to be saved using `Sleipnir.save_results_file!`, but this step is currently commented out and will be enabled once the optimization is working. Finally, the garbage collector is triggered to free up memory.

# Notes

  * The `Sleipnir.save_results_file!` function call is currently commented out and should be enabled once the optimization process is confirmed to be working.
  * The garbage collector is explicitly run using `GC.gc()` to manage memory usage.
