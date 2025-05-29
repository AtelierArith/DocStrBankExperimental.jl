```
solve_dopf_coordinated_mp(data::Dict{String, <:Any}, model_type::DataType, optimizer, dopf_method::Module; print_level::Int64=1, multiprocessors::Bool=false, mismatch_method::String="norm", tol::Float64=1e-4, max_iteration::Int64=1000, save_data::Vector{String}=[], kwargs...)
```

Solve OPF problem using distributed algorithm with central coordinator on multiprocessors. Multiprocessors feature requires loading the PowerModelsADA and the optimizer packages on all the processors using @everywhere using <package_name>.

# Arguments:

  * data::Dict{String, <:Any} : dictionary contains case in PowerModel format
  * model_type::DataType : power flow formulation (PowerModel type)
  * optimizer : optimizer JuMP initiation object
  * dopf_method::Module : module contains the distributed algorithm methods as follows:

      * initialize_method_local::Function : initialize the local algorithm parameters and shared variables
      * initialize_method_coordinator::Function : initialize the coordinator algorithm parameters and shared variables
      * update_method_local::Function : update the local data after each iteration
      * update_method_coordinator::Function : update the coordinator data after each iteration
      * build_method_local::Function : local problem formulation
      * build_method_coordinator::Function : coordinator problem formulation
  * print_level::Int64=1 : 0 - no print, 1 - print mismatch after each iteration and result summary, 2 - print optimizer output
  * mismatch_method::String="norm" : mismatch calculation method (norm, max)
  * tol::Float64=1e-4 : mismatch tolerance
  * max_iteration::Int64=1000 : maximum number of iteration
  * save*data::Vector{String}=[] : vector contains the keys of the dictionaries to be saved at each iteration in "previous\*solution". For example, save*data=["solution", "shared*variable", "mismatch"]
  * kwargs = includes algorithm-specific and initialization parameters
