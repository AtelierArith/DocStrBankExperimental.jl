```
spread(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Real; distance=Euclidean(), res=1.0)
spread(points::Matrix{<:Real}, initial::Real, friction::Real; distance=Euclidean(), res=1.0)
```

Optimized (and more accurate) function based on the same friction everywhere.

When the friction is the same everywhere, there's no need for searching the shortest cost path, as one can just take a direct line to the input points.

The calculated cost is more accurate, as there's no 'zigzag' from cell center to cell center.
