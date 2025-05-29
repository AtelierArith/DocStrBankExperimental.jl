```
solve_dopf_atc_coordinated(data::Dict{String, <:Any}, model_type::DataType, optimizer; tol::Float64=1e-4, 
max_iteration::Int64=1000, print_level = true, alpha::Real=1000)
```

Solve the distributed OPF problem using ATC algorithm with central coordinator.

# Arguments:

  * data::Dict{String, <:Any} : dictionary contains case in PowerModel format
  * model_type::DataType : power flow formulation (PowerModel type)
  * optimizer : optimizer JuMP initiation object
  * mismatch_method::String="norm" : mismatch calculation method (norm, max)
  * tol::Float64=1e-4 : mismatch tolerance
  * max_iteration::Int64=1000 : maximum number of iteration
  * print_level::Int64=1 : print mismatch after each iteration and result summary
  * alpha::Real=1.05 : algorithm parameters
  * beta::Real=1.0 : algorithm parameters
