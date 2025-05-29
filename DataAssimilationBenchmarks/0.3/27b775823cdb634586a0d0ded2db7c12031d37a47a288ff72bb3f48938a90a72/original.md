```
function ArView(type)
    Union{Array{T, 2}, SubArray{T, 2}} where T <: type
end
```

Type constructor for union of Arrays and SubArrays for use within ensemble conditioning operations, integration schemes and other array operations.
