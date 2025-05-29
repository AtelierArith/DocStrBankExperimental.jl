```
ArrayModel{T} <: AbstractMillModel
```

[`ArrayNode`](@ref)を処理するためのモデルノードです。それは、[`ArrayNode`](@ref)内のデータに対して、内部に保存されている（サブ）モデル`m`を適用します。

# 例

```jldoctest array_model
julia> Random.seed!(0);
```

```jldoctest array_model; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> n = ArrayNode(randn(Float32, 2, 2))
2×2 ArrayNode{Matrix{Float32}, Nothing}:
 0.94... 1.53...
 0.13... 0.12...
```

```jldoctest array_model
julia> m = ArrayModel(Dense(2, 2))
ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
```

```jldoctest array_model; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> m(n)
2×2 Matrix{Float32}:
 -0.50... -0.77...
  0.25...  0.49...
```

関連情報: [`AbstractMillModel`](@ref), [`ArrayNode`](@ref).
