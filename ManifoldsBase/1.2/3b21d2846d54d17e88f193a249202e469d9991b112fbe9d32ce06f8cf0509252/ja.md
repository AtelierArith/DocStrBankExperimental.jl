```
allocate_on(M::AbstractManifold, [T:::Type])
allocate_on(M::AbstractManifold, F::FiberType, [T:::Type])
```

マンifold `M` 上に新しい点を割り当て、オプションの型 `T` を指定します。`T` は [`allocate`](@ref) のような数値要素型ではなく、返される全体の点の型です。

`F` が提供されている場合、基点とは独立していると仮定して、対応するファイバーの要素が割り当てられます。

接ベクトルを割り当てるには、`` を使用します。

# 例

```julia-repl
julia> using ManifoldsBase

julia> M = ManifoldsBase.DefaultManifold(4)
DefaultManifold(4; field = ℝ)

julia> allocate_on(M)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, Array{Float64})
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, TangentSpaceType())
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

julia> allocate_on(M, TangentSpaceType(), Array{Float64})
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0

```
