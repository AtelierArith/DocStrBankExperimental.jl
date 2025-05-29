```
function VecA(type)
    Union{Vector{T}, SubArray{T, 1}} where T <: type
end
```

Type constructor for union of Vectors and 1-D SubArrays.  This is utilzed  in order to pass columns of an ensemble maxtrix into integration schemes and related array operations.
