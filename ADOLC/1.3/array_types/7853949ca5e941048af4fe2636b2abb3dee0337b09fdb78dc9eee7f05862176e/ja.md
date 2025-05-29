```
cxx_res_to_jl_res(cxx_res::CxxVector) 
cxx_res_to_jl_res(cxx_res::CxxMatrix)
cxx_res_to_jl_res(cxx_res::CxxTensor)
```

`Vector{Cdouble}`、`Matrix{Cdouble}`、または `Array{Cdouble, 3}` を作成し、指定された入力 `CxxVector`、`CxxMatrix`、または `CxxTensor` から値をコピーします。
