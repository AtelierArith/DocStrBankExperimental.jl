```
lr_ratio(dx::RealVector, e::Edge)::Float64
```

The ratio between the length of a vector `dx` and length of the edge `e`.  This may sound like a dubious function but is used so very often in this method. It is slightly faster than `norm(dx)/len(e)` because it computes only one square root.
