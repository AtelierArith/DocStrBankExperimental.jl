```
topk(o::PyObject, k::Union{PyObject,Integer}=1;
    sorted::Bool=true, name::Union{Nothing,String}=nothing)
```

Finds values and indices of the `k` largest entries for the last dimension. If `sorted=true` the resulting k elements will be sorted by the values in descending order.
