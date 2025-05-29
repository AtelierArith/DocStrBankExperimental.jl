```
trainables(x, path = false)
```

Return an iterable over all the trainable parameters in `x`, that is all the numerical arrays (see [`isnumeric`](@ref Optimisers.isnumeric)) which are reachable through [`trainable`](@ref Optimisers.trainable).

Parameters appearing multiple times in the model (tied weights) will be present only once in the output.

If `path = false`, the output is a list of numerical arrays.

If `path = true`, the output is a list of `(KeyPath, AbstractArray)` pairs, where [`KeyPath`](@ref) is a type representing the path to the array in the original structure.

See also [`destructure`](@ref) for a similar operation that returns a single flat vector instead.

# Examples

```jldoctest
julia> struct MyLayer
         w
         b
       end

julia> Functors.@functor MyLayer

julia> Optimisers.trainable(x::MyLayer) = (; w = x.w,) # only w is trainable in this example

julia> x = MyLayer([1.0,2.0,3.0], [4.0,5.0,6.0]);

julia> trainables(x)
1-element Vector{AbstractArray}:
 [1.0, 2.0, 3.0]

julia> x = MyLayer((a=[1.0,2.0], b=[3.0]), [4.0,5.0,6.0]);

julia> trainables(x) # collects nested parameters
2-element Vector{AbstractArray}:
 [1.0, 2.0]
 [3.0]
```

```jldoctest
julia> x = (a = [1.0,2.0], b = (Dict("c" => [3.0, 4.0], "d" => 5.0), [6.0,7.0]));

julia> for (kp, y) in trainables(x, path = true)
           println(kp, " => ", y)
       end
KeyPath(:a,) => [1.0, 2.0]
KeyPath(:b, 1, "c") => [3.0, 4.0]
KeyPath(:b, 2) => [6.0, 7.0]

julia> getkeypath(x, KeyPath(:b, 1, "c"))
2-element Vector{Float64}:
 3.0
 4.0
```
