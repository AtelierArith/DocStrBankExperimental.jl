```
print_c_array(io, sys::Vector{<:AbstractStateSpace}, t::AbstractVector, name = "sys"; cse = false, s = "", en = "", struct_name::Union{Nothing, String} = nothing, struct_type = nothing)
```

Write C-code for an interpolated linear system. The interpolation vector `t` defines the interpolation points, this vector is expected to be of the same length as the vector of linear systems `sys`. 

  * `s, en`: are strings that are appended at the start and end of variables names in the C-code.
  * `struct_name`: If provided, the interpolation matrices will be placed inside a struct with this name.
  * `struct_type`: If the struct name is used, provide also the C type of the struct.
