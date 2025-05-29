```
unembed(matrix::AbstractMatrix{<:Number}, subspace::AbstractVector{Int})
```

`matrix` からサブスペースオペレーターをアンエンベッドします。これは `matrix[subspace, subspace]` を呼び出すことと同等です。
