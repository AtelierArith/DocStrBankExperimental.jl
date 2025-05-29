```
Grid(dims::AbstractVector, G=Graph; periodic=false)
```

`d`次元の立方格子を作成します。ここで、`d=length(dims)` であり、次元 `i` における長さは `dims[i]` です。`periodic=true` の場合、結果として得られる格子は各次元で周期境界条件を持ちます。
