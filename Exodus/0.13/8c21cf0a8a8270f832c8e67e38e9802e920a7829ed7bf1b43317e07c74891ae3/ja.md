```julia
struct ExodusDatabase{M, I, B, F, Init}
```

  * `exo::Int32`
  * `mode::String`
  * `file_name::String`
  * `init::Any`
  * `block_name_dict::Dict{String}`
  * `nset_name_dict::Dict{String}`
  * `sset_name_dict::Dict{String}`
  * `element_var_name_dict::Dict{String}`
  * `global_var_name_dict::Dict{String}`
  * `nodal_var_name_dict::Dict{String}`
  * `nset_var_name_dict::Dict{String}`
  * `sset_var_name_dict::Dict{String}`
