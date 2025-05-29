```
acwt_heatmap(x::AbstractArray{<:Number,2})
```

Takes the natural log of the absolute value of each cell, and plots a heatmap. Can be used for visualizing an input image or the coefficient matrix of a 2D ACW decomposition.

# Arguments

  * `x::AbstractArray{<:Number,2}`: A image or a 2D matrix
