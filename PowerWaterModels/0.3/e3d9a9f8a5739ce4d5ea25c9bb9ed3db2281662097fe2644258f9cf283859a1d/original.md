```
solve_model(
    data, model_type, optimizer, build_method;
    ref_extensions, solution_processors, kwargs...)

Instantiates and solves the joint PowerWaterModels model from input data `data`, where
`model_type` is the power-water modeling type, `build_method` is the build method for
the problem specification being considered, `ref_extensions` is an array of power and
water modeling extensions, and `solution_processors` is an array of power and water
modeling solution data postprocessors. Returns a dictionary of model results.
```
