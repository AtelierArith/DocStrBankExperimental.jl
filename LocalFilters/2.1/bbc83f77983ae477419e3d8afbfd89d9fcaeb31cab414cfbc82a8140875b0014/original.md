```
opening(A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

yields an opening of array `A` by the structuring element defined by `B`. An opening is an erosion followed by a dilation. The result `dst` is an array similar to `A`.

See [`opening!`](@ref) for an in-place version of the method, [`closing`](@ref) for a related filter, and [`erode`](@ref) or [`dilate`](@ref) for a description of these operations and for the meaning of keywords.
