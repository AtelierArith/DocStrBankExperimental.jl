```
mis_compactify!(tropicaltensor; potential=nothing)
```

Compactify tropical tensor for maximum independent set problem. It will eliminate some entries by setting them to zero, by the criteria that removing these entry does not change the MIS size of its parent graph (reference to be added).

### Arguments

  * `tropicaltensor::AbstractArray{T}`: the tropical tensor

### Keyword arguments

  * `potential=nothing`: the maximum possible MIS contribution from each open vertex
