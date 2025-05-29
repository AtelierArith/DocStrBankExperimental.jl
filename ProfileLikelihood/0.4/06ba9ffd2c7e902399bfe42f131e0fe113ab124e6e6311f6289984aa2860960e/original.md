```
get_prediction_intervals(q, prof::(Bivariate)ProfileLikelihoodSolution, data;
    q_prototype=isinplace(q, 3) ? nothing : build_q_prototype(q, prof, data), resolution=250)
```

Obtain prediction intervals for the output of the prediction function `q`, assuming `q` returns (or operates in-place on) a vector.

# Arguments

  * `q`: The prediction function, taking either the form `(θ, data)` or `(cache, θ, data)`. The former version is an out-of-place version, returning the full vector, while the latter version is an in-place version, with the output being placed into `cache`. The argument `θ` is the same as the parameters used in the likelihood problem (from `prof`), and the `data` argument is the same `data` as in this function.
  * `prof::(Bivariate)ProfileLikelihoodSolution`: The profile likelihood results.
  * `data`: The argument `data` in `q`.

# Keyword Arguments

  * `q_prototype=isinplace(q, 3) ? nothing : build_q_prototype(q, prof, data)`: A prototype for the result of `q`. If you are using the `q(θ, data)` version of `q`, this can be inferred from `build_q_prototype`, but if you are using the in-place version then a `build_q_prototype` is needed. For example, if `q` returns a vector with eltype `Float64` and has length 27, `q_prototype` could be `zeros(27)`.
  * `resolution::Integer=250`: The amount of curves to evaluate for each parameter. This will be the same for each parameter. If `prof isa BivariateProfileLikelihoodSolution`, then `resolution^2` points are defined inside a bounding box for the confidence region, and then we throw away all points outside of the actual confidence region.
  * `parallel=false`: Whether to use multithreading. Multithreading is used when building `q_vals` below.

# Outputs

Four values are returned. In order: 

  * `individual_intervals`: Prediction intervals for the output of `q`, relative to each parameter.
  * `union_intervals`: The union of the individual prediction intervals from `individual_intervals`.
  * `q_vals`: Values of `q` at each parameter considered. The output is a `Dict`, where the parameter index is mapped to a matrix where each column is an output from `q`, with the `j`th column corresponding to the parameter value at `param_ranges[j]`.
  * `param_ranges`: Parameter values used for each prediction interval.
