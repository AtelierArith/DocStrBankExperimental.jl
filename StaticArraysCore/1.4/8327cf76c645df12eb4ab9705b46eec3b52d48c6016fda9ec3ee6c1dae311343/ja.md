```
abstract FieldVector{N, T} <: FieldArray{Tuple{N}, 1}
```

この型を継承することで、自分自身のベクトル型を簡単に作成できます。`FieldVector`は自動的に`getindex`と`setindex!`を適切に定義します。不変の`FieldVector`は、同様の長さと要素型の`SVector`と同じくらいの性能を持ち、可変の`FieldVector`は`MVector`と同様に振る舞います。

要素型に対してパラメトリックな`FieldVector`を定義する場合、配列操作を通じて配列型を保持するために`similar_type`を定義することを検討してください。以下の例のように。

# 例

```
struct Vec3D{T} <: FieldVector{3, T}
    x::T
    y::T
    z::T
end

StaticArrays.similar_type(::Type{<:Vec3D}, ::Type{T}, s::Size{(3,)}) where {T} = Vec3D{T}
```
