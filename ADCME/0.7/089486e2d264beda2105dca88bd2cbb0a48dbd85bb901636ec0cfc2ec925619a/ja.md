```
accumulate(handle::PyObject, row::Union{PyObject, <:Integer}, cols::Union{PyObject, Array{<:Integer}}, vals::Union{PyObject, Array{<:Real}})
```

`row`-行を累積します。値をスパース行列に追加します。

```julia
for k = 1:length(cols)
    A[row, cols[k]] += vals[k]
end
```

`handle`は[`SparseAssembler`](@ref)によって作成されたハンドルです。

例については[`SparseAssembler`](@ref)を参照してください。

!!! note
    関数`accumulate`は`op::PyObject`を返します。`op`が実行されるときにのみ、非ゼロの値がスパース行列に格納されます。

