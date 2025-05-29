```
axes1d(size::NTuple{N, Int}; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}
は、すべてがx方向に向いている軸のタプルを返します。
これはプロットに非常に便利です（下の例を参照してください）。
オプションの引数 `keepdims` を使用すると、`meshgrid` 操作に類似した、ブロードキャスティングとジェネレーターのパフォーマンスをサポートする方向性のある1次元ベクトルを取得できます。
他のオプションの説明については `rr2` を参照してください。
```

```jldoctest
julia> using Plots, IndexFunArrays

julia> sz = (200,100);

julia> heatmap(axes1d(sz)..., rr(sz)')

julia> x,y = axes1d((10,11), keepdims=true)
"hi" = "hi"
Base.Generator{Tuple{Int64, Int64}, IndexFunArrays.var"#675#677"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}(IndexFunArrays.var"#675#677"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Int64, Int64}}((6, 6), (1, 1), (10, 11)), (1, 2))

julia> size(y)
(1, 11)
```

---

axes1d(arr::AbstractArray{T, N}; offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}

これは `axes1d(size(arr); offset=CtrFT, scale=ScaUnit, dims=ntuple(+, N), accumulator=sum, weight=1) where {N}` のラッパーです。 ```
