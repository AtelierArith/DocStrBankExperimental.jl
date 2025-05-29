```
pathlength(p::Path)
pathlength(array::AbstractArray{Node{T}}) where {T}
pathlength(array::AbstractArray{T}) where {T<:Segment}
pathlength(node::Node)
```

パスの物理的な長さ。`length`はパス内のセグメントの数を返すことに注意してください。パスの物理的な長さではありません。
