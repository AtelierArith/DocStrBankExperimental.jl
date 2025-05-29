```
closing(A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

yields a closing of array `A` by the structuring element defined by `B`. A closing is a dilation followed by an erosion. The result `dst` is an array similar to `A`.

See [`closing!`](@ref) for an in-place version of the method, [`opening`](@ref) for a related filter, and [`erode`](@ref) or [`dilate`](@ref) for a description of these operations and for the meaning of keywords.
