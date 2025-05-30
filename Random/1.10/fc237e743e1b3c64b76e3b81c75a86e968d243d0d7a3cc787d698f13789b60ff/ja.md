```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

スケール1の指数分布に従って、型 `T` のランダムな数を生成します。オプションで、そのようなランダムな数の配列を生成します。`Base` モジュールは現在、[`Float16`](@ref)、[`Float32`](@ref)、および [`Float64`](@ref)（デフォルト）の型に対する実装を提供しています。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> randexp(rng, Float32)
2.4835055f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.5167    1.30652   0.344435
 0.604436  2.78029   0.418516
 0.695867  0.693292  0.643644
```
