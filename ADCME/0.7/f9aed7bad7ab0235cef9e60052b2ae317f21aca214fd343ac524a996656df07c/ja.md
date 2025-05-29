```
vector(i::Union{Array{T}, PyObject, UnitRange, StepRange}, v::Union{Array{Float64},PyObject},s::Union{Int64,PyObject})
```

長さ `s` のベクトル `V` を返します。次のように定義されます。

```
V[i] = v
```
