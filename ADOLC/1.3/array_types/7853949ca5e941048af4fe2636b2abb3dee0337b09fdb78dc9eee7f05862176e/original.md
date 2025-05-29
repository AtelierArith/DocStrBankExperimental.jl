```
cxx_res_to_jl_res(cxx_res::CxxVector) 
cxx_res_to_jl_res(cxx_res::CxxMatrix)
cxx_res_to_jl_res(cxx_res::CxxTensor)
```

Creates a `Vector{Cdouble}`, `Matrix{Cdouble}` or `Array{Cdouble, 3}` and copies the values from the given input `CxxVector`, `CxxMatrix` or `CxxTensor` to it.
