```julia
function statistic(x::IntVec, y::UniData, stat::StudentT_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...)
```

独立サンプルのためのスチューデントの *t* 統計量、参照：[Edgington (1995)](@ref "References")、p. 3。

`stat` と例を除くすべての引数については、上記の `AnovaF_IS` の [`statistic`](@ref) メソッドを参照してください。
