```
value_flatten([eltype=Float64], x)
```

`flatten`と似たように動作しますが、返される`unflatten`関数は、値がアンラップされた`x`のようなオブジェクトを返します。

次のように行うことは

```julia
v, unflatten = value_flatten(x)
```

次のように行うことと同じです

```julia
v, _unflatten = flatten(x)
unflatten = ParameterHandling.value ∘ _unflatten
```
