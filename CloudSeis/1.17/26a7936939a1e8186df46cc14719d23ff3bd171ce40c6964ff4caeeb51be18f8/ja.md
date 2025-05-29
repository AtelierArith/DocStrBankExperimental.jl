```
fold(io::CSeis, i)
```

CloudSeisフレームに対応するfoldを返し、フレームはそのインデックス`i`によって説明されます。フレームインデックスは`Int`、`VarArg{Int}`、または`CartesianIndex`のいずれかであることができます。

# 例

```julia
io = csopen("foo.cs", "w"; axis_lengths=[10,11,12])
fold(io, 5, 6) # 5番目のフレームと6番目のボリュームに対応するfold
```
