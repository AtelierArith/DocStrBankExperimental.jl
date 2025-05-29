```
Halfspace(normal::AbstractVector{T} [, origin::AbstractVector{T}=zeros()])
```

すべての点 $\mathbf x$ によって定義される半空間は、$(\mathbf x - \mathbf o) \cdot \mathbf n < 0$ を満たすものであり、ここで $\mathbf n$ は単位法線、$\mathbf o$ は原点です。
