```
struct TransientReduction{A,B,RS<:Reduction{A,B},RT<:Reduction{A,EuclideanNorm}} <: Reduction{A,B}
  reduction_space::RS
  reduction_time::RT
end
```

Wrapper for reduction methods in transient problems. The fields `reduction_space` and `reduction_time` respectively represent the spatial reduction method, and the temporal one
