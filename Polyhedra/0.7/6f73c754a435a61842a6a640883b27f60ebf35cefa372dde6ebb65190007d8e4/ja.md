```
center_of_mass(p::Polyhedron{T}) where {T}
```

`p`の質量中心を返します。これは、長さ`fulldim(p)`の`Vector{T}`として表されます。`p`が退化している場合はエラーをスローします。
