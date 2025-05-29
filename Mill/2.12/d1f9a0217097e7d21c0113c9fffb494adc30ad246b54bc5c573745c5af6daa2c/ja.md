```
ProductModel(ms, m=identity)
ProductModel(m=identity; ms...)
```

引数から[`ProductModel`](@ref)を構築します。`ms`は1つ以上の[`AbstractMillModel`](@ref)sのイテラブル（`Tuple`、`NamedTuple`または`Vector`）である必要があります。

`ms`の要素として任意の関数を渡すことも可能です。その場合、それは[`ArrayNode`](@ref)にラップされます。

# 例

```jldoctest
julia> ProductModel(a=ArrayModel(Dense(2, 2)), b=identity)
ProductModel ↦ identity
  ├── a: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
  ╰── b: ArrayModel(identity)

julia> ProductModel(Dense(4, 2); a=ArrayModel(Dense(2, 2)), b=Dense(2, 2))
ProductModel ↦ Dense(4 => 2)  2 arrays, 10 params, 128 bytes
  ├── a: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
  ╰── b: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> ProductModel((identity, BagModel(ArrayModel(Dense(2, 2)), SegmentedMean(2), identity)))
ProductModel ↦ identity
  ├── ArrayModel(identity)
  ╰── BagModel ↦ SegmentedMean(2) ↦ identity  1 arrays, 2 params (all zero), 48 bytes
        ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> ProductModel(identity)
ProductModel ↦ identity
  ╰── ArrayModel(identity)
```

参照: [`AbstractMillModel`](@ref), [`AbstractProductNode`](@ref), [`ProductNode`](@ref).
