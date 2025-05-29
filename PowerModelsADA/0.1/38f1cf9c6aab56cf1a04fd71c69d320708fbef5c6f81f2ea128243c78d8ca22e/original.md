```
solve_dopf_aladin_coordinated(data::Dict{String, <:Any}, model_type::DataType, optimizer; tol::Float64=1e-4, 
max_iteration::Int64=1000, print_level = true, p::Real=1000, mu::Real=1000, p_upper::Real=1e6, mu_upper::Real=2e6, r_p::Real=1.5, mu_p::Real=2, a1::Real=1, a2::Real=1, #     a3::Real=1, q_gamma::Real=0, sigma::Dict{String,Real}=Dict())
```

Solve the distributed OPF problem using ALADIN algorithm with central coordinator.

# Arguments:

  * data::Dict{String, <:Any} : dictionary contains case in PowerModel format
  * model_type::DataType : power flow formulation (PowerModel type)
  * optimizer : optimizer JuMP initiation object
  * mismatch_method::String="norm" : mismatch calculation method (norm, max)
  * tol::Float64=1e-4 : mismatch tolerance
  * max_iteration::Int64=1000 : maximum number of iteration
  * print_level::Int64=1 : print mismatch after each iteration and result summary
  * p::Real=1000 : parameter
  * mu::Real=1000 : parameter
  * p_upper::Real=1e6 : parameter
  * mu_upper::Real=2e6 : parameter
  * r_p::Real=1.5 : parameter
  * r_mu::Real=2 : parameter
  * a1::Real=1 : parameter
  * a2::Real=1 : parameter
  * a3::Real=1 : parameter
  * q_gamma::Real=0 : parameter
  * sigma::Dict{String, <:Any}=Dict() : dictionary with variable name as key and parameter value as values
