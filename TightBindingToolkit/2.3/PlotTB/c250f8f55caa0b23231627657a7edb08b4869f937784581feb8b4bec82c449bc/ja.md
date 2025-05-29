```julia
plot_band_structure!(M<:Union{Model, BdGModel}, path::Vector{Vector{Float64}},  band_index::Vector{Int64} = collect(1:length(M.Ham.bands[begin])) ; labels::Vector{} = repeat([""], length(path)), closed::Bool=true, nearest::Bool=true) --> Plots.plot()
```

`Model`のバンド構造を、与えられた臨界点によって決定されたBZ内の`path`に沿ってプロットするための関数です。複数のバンドを`band_index`に考慮することができます。`labels`は臨界点のプロットラベルです。
