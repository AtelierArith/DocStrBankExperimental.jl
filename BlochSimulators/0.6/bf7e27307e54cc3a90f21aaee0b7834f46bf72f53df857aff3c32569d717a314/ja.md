```
struct Isochromat{T<:Real} <: FieldVector{3,T}
    x::T
    y::T
    z::T
end
```

スピンアイソクロマットのx,y,z成分をカスタムフィールド名を持つ`StaticVector`（パッケージ`StaticArrays`から）であるFieldVectorに保持します。
