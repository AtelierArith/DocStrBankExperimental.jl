```
batch(xs)
```

Batch the arrays in `xs` into a single array with  an extra dimension.

If the elements of `xs` are tuples, named tuples, or dicts,  the output will be of the same type. 

See also [`unbatch`](@ref) and [`batch_sequence`](@ref).

# Examples

```jldoctest
julia> batch([[1,2,3], 
              [4,5,6]])
3×2 Matrix{Int64}:
 1  4
 2  5
 3  6

julia> batch([(a=[1,2], b=[3,4])
               (a=[5,6], b=[7,8])]) 
(a = [1 5; 2 6], b = [3 7; 4 8])
```
