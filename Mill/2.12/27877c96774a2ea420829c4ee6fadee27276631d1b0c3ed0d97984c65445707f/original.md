```
catobs(ns...)
```

Merge multiple nodes storing samples (observations) into one suitably promoting in the process if possible.

Similar to `Base.cat` but concatenates along the abstract "axis" where samples are stored.

In case of repeated calls with varying number of arguments or argument types, use `reduce(catobs, [ns...])` to save compilation time.

# Examples

```jldoctest
julia> catobs(ArrayNode(zeros(2, 2)), ArrayNode([1 2; 3 4]))
2×4 ArrayNode{Matrix{Float64}, Nothing}:
 0.0  0.0  1.0  2.0
 0.0  0.0  3.0  4.0

julia> n = ProductNode(t1=ArrayNode(randn(2, 3)), t2=BagNode(ArrayNode(randn(3, 8)), bags([1:3, 4:5, 6:8])))
ProductNode  3 obs
  ├── t1: ArrayNode(2×3 Array with Float64 elements)  3 obs
  ╰── t2: BagNode  3 obs
            ╰── ArrayNode(3×8 Array with Float64 elements)  8 obs

julia> catobs(n[1], n[3])
ProductNode  2 obs
  ├── t1: ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── t2: BagNode  2 obs
            ╰── ArrayNode(3×6 Array with Float64 elements)  6 obs
```
