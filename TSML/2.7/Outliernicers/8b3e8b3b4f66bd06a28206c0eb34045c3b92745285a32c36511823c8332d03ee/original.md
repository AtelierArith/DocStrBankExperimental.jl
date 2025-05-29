```
transform!(st::Outliernicer, features::T) where {T<:Union{Vector,Matrix,DataFrame}}
```

Locate outliers based on IQR factor and calls DateValNNer to replace them with nearest neighbors.
