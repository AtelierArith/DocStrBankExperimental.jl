```
solve_model(p_file, w_file, link_file, model_type, optimizer, build_method; kwargs...)

Instantiates and solves a PowerWaterModels modeling object from power and water input
files `p_file` and `w_file`. Additionally, `link_file` is an input file that links
power and water networks, `model_type` is the power-water modeling type, and
`build_method` is the build method for the problem specification being considered.
Returns a dictionary of model results.
```
