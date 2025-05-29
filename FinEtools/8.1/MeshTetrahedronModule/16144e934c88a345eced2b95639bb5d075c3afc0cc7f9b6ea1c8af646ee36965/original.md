```
T10layeredplatex(
    xs::VecOrMat{T},
    ys::VecOrMat{T},
    ts::VecOrMat{T},
    nts::VecOrMat{IT},
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

T10 mesh for a layered block (composite plate) with specified in plane coordinates.

xs,ys =Locations of the individual planes of nodes. ts= Array of layer thicknesses, nts= array of numbers of elements per layer

The finite elements of each layer are labeled with the layer number, starting from 1 at the bottom.
