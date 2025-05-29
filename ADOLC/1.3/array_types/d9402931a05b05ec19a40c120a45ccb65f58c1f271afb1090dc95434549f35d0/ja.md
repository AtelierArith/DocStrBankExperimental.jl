```
jl_res_to_cxx_res!(cxx_res::CxxVector, jl_res::AbstractVector{Cdouble}) 
jl_res_to_cxx_res!(cxx_res::CxxMatrix, jl_res::AbstractMatrix{Cdouble})
jl_res_to_cxx_res!(cxx_res::CxxTensor, jl_res::AbstractArray{Cdouble, 3})
```

`AbstractVector{Cdouble}`、`AbstractMatrix{Cdouble}`、または `AbstractArray{Cdouble, 3}` の値を対応する `CxxVector`、`CxxMatrix`、または `CxxTensor` にコピーします。
