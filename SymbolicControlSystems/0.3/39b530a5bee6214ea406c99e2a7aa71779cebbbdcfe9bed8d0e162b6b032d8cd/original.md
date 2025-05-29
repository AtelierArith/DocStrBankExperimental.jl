```
print_c_array(io, a::Vector{<:AbstractArray}, t::AbstractVector, name = "mat"; cse = false, s = "", print_vector = true, print_logic = true, struct_name::Union{Nothing, String} = nothing, struct_type = nothing, ivecname = name * "_interp_vect")
```

Write C-code for interpolating between arrays `a`. The array `t` contains the interpolation points.
