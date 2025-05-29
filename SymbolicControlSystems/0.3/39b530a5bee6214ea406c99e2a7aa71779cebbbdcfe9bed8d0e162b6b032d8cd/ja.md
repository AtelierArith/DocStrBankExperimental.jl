```
print_c_array(io, a::Vector{<:AbstractArray}, t::AbstractVector, name = "mat"; cse = false, s = "", print_vector = true, print_logic = true, struct_name::Union{Nothing, String} = nothing, struct_type = nothing, ivecname = name * "_interp_vect")
```

配列 `a` の間で補間するための C コードを書いてください。配列 `t` には補間点が含まれています。
