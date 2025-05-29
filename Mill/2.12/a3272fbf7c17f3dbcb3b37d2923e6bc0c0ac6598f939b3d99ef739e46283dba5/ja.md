```
ProductModel{T <: Mill.VecOrTupOrNTup{<:AbstractMillModel}, U} <: AbstractMillModel
```

[`ProductNode`](@ref)を処理するためのモデルノードです。データノードの各サブツリーに対して、`ms`から1つの（サブ）モデルを適用し、結果の連結に対して`m`を適用します。

# 例

```jldoctest product_model
julia> Random.seed!(0);

julia> n = ProductNode(a=ArrayNode([0 1; 2 3]), b=ArrayNode([4 5; 6 7]))
ProductNode  2 obs
  ├── a: ArrayNode(2×2 Array with Int64 elements)  2 obs
  ╰── b: ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> m1 = ProductModel(a=ArrayModel(Dense(2, 2)), b=ArrayModel(Dense(2, 2)))
ProductModel ↦ identity
  ├── a: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
  ╰── b: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
```

```jldoctest product_model; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> m1(n)
4×2 Matrix{Float32}:
 -2.36...  -3.58...
 -2.11...  -3.40...
 -6.31...  -7.61...
 -2.54...  -2.66...
```

```jldoctest product_model
julia> m2 = ProductModel(a=identity, b=identity)
ProductModel ↦ identity
  ├── a: ArrayModel(identity)
  ╰── b: ArrayModel(identity)

julia> m2(n)
4×2 Matrix{Int64}:
 0  1
 2  3
 4  5
 6  7
```

参照: [`AbstractMillModel`](@ref), [`AbstractProductNode`](@ref), [`ProductNode`](@ref).
