```
jl_res_to_cxx_res!(cxx_res::CxxVector, jl_res::AbstractVector{Cdouble}) 
jl_res_to_cxx_res!(cxx_res::CxxMatrix, jl_res::AbstractMatrix{Cdouble})
jl_res_to_cxx_res!(cxx_res::CxxTensor, jl_res::AbstractArray{Cdouble, 3})
```

Copies the values of a `AbstractVector{Cdouble}`, `AbstractMatrix{Cdouble}` or `AbstractArray{Cdouble, 3}` to a corresponding `CxxVector`, `CxxMatrix` or `CxxTensor`.
