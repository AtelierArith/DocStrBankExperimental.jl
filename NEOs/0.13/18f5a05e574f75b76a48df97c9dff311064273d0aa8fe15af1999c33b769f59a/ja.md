```
project(y::Vector{TaylorN{T}}, fit::LeastSquaresFit{T}) where {T <: Real}
```

`fit`の共分散行列を`y`に射影します。
