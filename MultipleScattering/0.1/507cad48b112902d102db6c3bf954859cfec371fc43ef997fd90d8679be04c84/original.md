```
Plate(normal::AbstractVector{T}, width::T, [, origin::AbstractVector{T}=zeros()])
```

A plate defined by all the points $\mathbf x$ that satify $|(\mathbf x - \mathbf o) \cdot \mathbf n| < w /2$ where $\mathbf n$ is the unit normal, $\mathbf o$ is the origin, and $w$ is the width.
