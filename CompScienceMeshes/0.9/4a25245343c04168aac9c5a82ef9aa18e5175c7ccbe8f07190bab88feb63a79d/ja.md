```
skeleton(mesh, dim)
```

`mesh`の`dim`次元のサブセルからなるメッシュを返します。例えば、与えられたサーフェス`mesh`のエッジを取得するには、

```julia
edges = skelton(mesh, 1)
```
