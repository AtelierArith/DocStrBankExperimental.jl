```
create_matrix_templates(n_states::Vector{Int64}, n_observations::Vector{Int64}, n_controls::Vector{Int64}, policy_length::Int64, template_type::String = "uniform")
```

Creates templates for the A, B, C, D, and E matrices based on the specified parameters.

# Arguments

  * `n_states::Vector{Int64}`: A vector specifying the dimensions and number of states.
  * `n_observations::Vector{Int64}`: A vector specifying the dimensions and number of observations.
  * `n_controls::Vector{Int64}`: A vector specifying the number of controls per factor.
  * `policy_length::Int64`: The length of the policy sequence.
  * `template_type::String`: The type of templates to create. Can be "uniform", "random", or "zeros". Defaults to "uniform".

# Returns

  * `A, B, C, D, E`: The generative model as matrices and vectors.
