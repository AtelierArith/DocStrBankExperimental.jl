```
Mahalanobis_distance!{tp}(d::Array{tp, 1}, x::AbstractArray{tp, 2}, Q::AbstractArray{tp, 2}, i::Int, j::Int, dim::Int = 1)
```

compute the Euclidean distance between x[i,:] and x[j,:] and write the result to d. Memory efficient. dim is the dimension of i and j.
