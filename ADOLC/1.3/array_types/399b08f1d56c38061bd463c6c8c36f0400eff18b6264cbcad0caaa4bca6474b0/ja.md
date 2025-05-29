```
jl_res_to_cxx_res(jl_res::AbstractVector{Cdouble}) 
jl_res_to_cxx_res(jl_res::AbstractMatrix{Cdouble})
jl_res_to_cxx_res(jl_res::AbstractArray{Cdouble, 3})
```

`CxxVector`、`CxxMatrix`、または `CxxTensor` を作成し、与えられた入力 `AbstractVector{Cdouble}`、`AbstractMatrix{Cdouble}`、または `AbstractArray{Cdouble, 3}` から値をコピーします。
