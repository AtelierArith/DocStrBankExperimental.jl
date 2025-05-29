```
unembed(matrix::AbstractMatrix{<:Number}, subspace::AbstractVector{Int})
```

`matrix`から部分空間演算子をアンエンベッドします。これは`matrix[subspace, subspace]`を呼び出すのと同等です。
