```
solve_dopf_app(data::Dict{String, <:Any}, model_type::DataType, optimizer; 
mismatch_method::String="norm",tol::Float64=1e-4, max_iteration::Int64=1000, 
print_level::Int64=1, alpha::Real=1000, beta::Real, gamma::Real)
```

Solve the distributed OPF problem using APP algorithm.

# Arguments:

  * data::Dict{String, <:Any} : dictionary contains case in PowerModel format
  * model_type::DataType : power flow formulation (PowerModel type)
  * optimizer : optimizer JuMP initiation object
  * mismatch_method::String="norm" : mismatch calculation method (norm, max)
  * tol::Float64=1e-4 : mismatch tolerance
  * max_iteration::Int64=1000 : maximum number of iteration
  * print_level::Int64=1 : print mismatch after each iteration and result summary
  * alpha::Real=1000 : algorithm parameter
  * beta::Real=2alpha : algorithm parameter
  * gamma::Real=alpha : algorithm parameter
