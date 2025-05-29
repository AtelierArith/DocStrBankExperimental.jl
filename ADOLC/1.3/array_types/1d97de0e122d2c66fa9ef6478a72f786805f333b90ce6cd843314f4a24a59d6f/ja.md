```
cxx_res_to_jl_res!(jl_res::AbstractVector{Cdouble}, cxx_res::CxxVector)
cxx_res_to_jl_res!(jl_res::AbstractMatrix{Float64}, cxx_res::CxxMatrix)
cxx_res_to_jl_res!(jl_res::AbstractArray{Float64, 3}, cxx_res::CxxTensor)
```

`CxxVector`、`CxxMatrix`、または`CxxTensor`のエントリを`AbstractVector{Cdouble}`、`AbstractMatrix{Cdouble}`、または`AbstractArray{Cdouble, 3}`にコピーします。
