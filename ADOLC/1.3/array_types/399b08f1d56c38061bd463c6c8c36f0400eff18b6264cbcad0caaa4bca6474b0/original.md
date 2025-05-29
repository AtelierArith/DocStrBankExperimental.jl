```
jl_res_to_cxx_res(jl_res::AbstractVector{Cdouble}) 
jl_res_to_cxx_res(jl_res::AbstractMatrix{Cdouble})
jl_res_to_cxx_res(jl_res::AbstractArray{Cdouble, 3})
```

Creates a `CxxVector`, `CxxMatrix` or `CxxTensor` and copies the values from the given input `AbstractVector{Cdouble}`, `AbstractMatrix{Cdouble}` or `AbstractArray{Cdouble, 3}` to it.
