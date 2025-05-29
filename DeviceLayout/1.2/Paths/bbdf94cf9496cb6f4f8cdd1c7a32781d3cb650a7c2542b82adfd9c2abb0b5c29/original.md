```
pathlength(p::Path)
pathlength(array::AbstractArray{Node{T}}) where {T}
pathlength(array::AbstractArray{T}) where {T<:Segment}
pathlength(node::Node)
```

Physical length of a path. Note that `length` will return the number of segments in a path, not the physical length of the path.
