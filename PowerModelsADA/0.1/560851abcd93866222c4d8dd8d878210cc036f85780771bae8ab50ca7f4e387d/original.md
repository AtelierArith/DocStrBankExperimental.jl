```
solve_dopf(data::Dict{String, <:Any}, model_type::DataType, optimizer, dopf_method::Module; print_level::Int64=1, multiprocessors::Bool=false, mismatch_method::String="norm", tol::Float64=1e-4, max_iteration::Int64=1000, save_data::Vector{String}=[], kwargs...)
```

Solve OPF problem using fully distributed algorithm.

# Arguments:

  * data::Dict{String, <:Any} : dictionary contains case in PowerModel format
  * model_type::DataType : power flow formulation (PowerModel type)
  * optimizer : optimizer JuMP initiation object
  * dopf_method::Module : module contains the distributed algorithm methods as follows:

      * initialize_method::Function : initialize the algorithm parameters and shared variables
      * update_method::Function : update the algorithm after each iteration
      * build_method::Function : problem formulation
  * print_level::Int64=1 : 0 - no print, 1 - print mismatch after each iteration and result summary, 2 - print optimizer output
  * multiprocessors::Bool=false : enable multiprocessors using available workers. Multiprocessors feature requires loading the PowerModelsADA and the optimizer packages on all the processors using @everywhere using <package_name>.
  * mismatch_method::String="norm" : mismatch calculation method (norm, max)
  * tol::Float64=1e-4 : mismatch tolerance
  * max_iteration::Int64=1000 : maximum number of iteration
  * save*data::Vector{String}=[] : vector contains the keys of the dictionaries to be saved at each iteration in "previous*solution". For example, save*data=["solution", "shared*variable", "mismatch"]
  * kwargs = includes algorithm-specific and initialization parameters
