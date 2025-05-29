```
This function simulate the RF process over a set of graphs, within a range of probabilities.
Parameters:
    - samples_models::Vector{<:SirModel} => a set of SirModels,
    - first_infected => the set of first infected nodes,
    - ε::Float64 => the granularity of the probabilities to be considered (default = 0.01),
    - probs_limits::Tuple => the probability limits within which to simulate (default = (1.0e-6, 1 - 1.0e-6)),
    - plot_result => flag for plotting the result graph (dafult = false)
    - log => flag to get information about the simulation status (dafult = true)
Output: 
    infected => percentage of total infected for each contagion probabilitiy in the probabilities range
    standard_deviation => the standard deviation of the infected for each probabilitiy
    time => the average time to finish the Reed-Frost process, for each probabilitiy
```
