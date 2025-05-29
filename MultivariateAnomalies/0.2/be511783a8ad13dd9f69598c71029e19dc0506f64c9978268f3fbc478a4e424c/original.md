```
Dist2Centers(centers::AbstractArray{tp, 2}) where {tp}
```

Compute the distance to the nearest centers of i.e. a K-means clustering output. Large Distances to the nearest center are anomalies. data: Observations * Variables.

# Example

`(proj, targetValue)`
