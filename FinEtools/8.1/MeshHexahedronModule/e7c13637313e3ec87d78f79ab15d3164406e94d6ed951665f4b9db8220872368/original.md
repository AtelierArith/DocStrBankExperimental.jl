```
H8layeredplatex(xs::Vector{T}, ys::Vector{T}, ts::Vector{T}, nts::Vector{IT}) where {T<:Number, IT<:Integer}
```

H8 mesh for a layered block (composite plate) with specified in plane coordinates.

xs,ys =Locations of the individual planes of nodes. ts= Array of layer thicknesses, nts= array of numbers of elements per layer

The finite elements of each layer are labeled with the layer number, starting from 1.
