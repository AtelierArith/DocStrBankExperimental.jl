```
Plate(normal::AbstractVector{T}, width::T, [, origin::AbstractVector{T}=zeros()])
```

すべての点 $\mathbf x$ によって定義されるプレートで、$|(\mathbf x - \mathbf o) \cdot \mathbf n| < w /2$ を満たします。ここで、$\mathbf n$ は単位法線、$\mathbf o$ は原点、$w$ は幅です。
