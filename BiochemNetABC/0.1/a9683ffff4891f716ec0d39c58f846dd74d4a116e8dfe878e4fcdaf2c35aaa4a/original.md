`simulate(pm::ParametricModel, p_prior::AbstractVector{Float64})`

Simulates the model contained in the parametric model `pm` with the `p_prior` parameters. It simulates the model by taking the parameters contained in `get_proba_model(pm).p` and replace the 1D parameters pm.params with `p_prior`.
