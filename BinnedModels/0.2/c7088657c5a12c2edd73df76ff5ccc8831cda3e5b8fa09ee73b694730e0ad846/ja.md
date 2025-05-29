```
binned_likelihood(f_expectation, edges::Tuple{AbstractVector,...}, data::AbstractVector{<:Integer})
binned_likelihood(f_expectation, h::StatsBase.Histogram{<:Integer})
```

[DensityInterface](https://github.com/JuliaMath/DensityInterface.jl) APIと互換性のあるビン化された尤度オブジェクトを構築します。

また、[`binned_model`](@ref)も参照してください。
