```
insym(c::VertexModel)::Vector{Symbol}
insym(c::EdgeModel)::@NamedTuple{src::Vector{Symbol}, dst::Vector{Symbol}}
```

[`hasinsym`](@ref)/[`hasindim`](@ref) が true を返した *後* に呼び出す必要があります。`insym` ベクトルを返します。頂点モデルの場合は単一のベクトル、エッジの場合は二つのシンボルベクトルを持つ名前付きタプル `(; src, dst)` を返します。
