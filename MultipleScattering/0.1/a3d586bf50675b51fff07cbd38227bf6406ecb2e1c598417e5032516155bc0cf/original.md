```
Halfspace(normal::AbstractVector{T} [, origin::AbstractVector{T}=zeros()])
```

A halfspace defined by all the points $\mathbf x$ that satify $(\mathbf x - \mathbf o) \cdot \mathbf n < 0$ where $\mathbf n$ is the unit normal and $\mathbf o$ is the origin.
