```
assemble(m::Union{PyObject, <:Integer}, n::Union{PyObject, <:Integer}, ops::PyObject)
```

`ops`によって作成されたスパース行列を組み立てます。`ops`は、`accumulate`からの単一の出力であるか、いくつかの`ops`から連結されたものです。

```julia
op1 = accumulate(handle, 1, [1;2;3], [1.0;2.0;3.0])
op2 = accumulate(handle, 2, [1;2;3], [1.0;2.0;3.0])
op = [op1;op2] # equivalent to `vcat([op1, op2]...)`
```

`m`と`n`はスパース行列の行と列です。

例については[`SparseAssembler`](@ref)を参照してください。
