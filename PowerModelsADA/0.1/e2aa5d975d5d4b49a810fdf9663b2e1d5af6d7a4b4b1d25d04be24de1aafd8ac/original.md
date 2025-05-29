```
initialize_all_variable(data::Dict{String, <:Any}, model_type::DataType, dics_name::String="solution", initialization_method::String="flat")
```

return a dictionary contains all the problem variables. can be used to store the solutions.

# Arguments:

  * data::Dict{String, <:Any} : area data
  * model_type::DataType : power flow formulation (PowerModel type)
  * dics_name::String="solution" : location of existing dicrionary to be used to worm start the output
  * initialization_method::String="flat" : "flat" or "worm" initialization
