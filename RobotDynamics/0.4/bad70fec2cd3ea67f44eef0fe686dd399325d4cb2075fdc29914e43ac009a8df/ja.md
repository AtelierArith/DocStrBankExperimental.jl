```
KnotPoint{Nx,Nu,V,T}
```

可変の [`AbstractKnotPoint`](@ref) で、`Nx` の状態、`Nu` の制御を持ち、データ型 `T` のベクトル型 `V` を使用して保存されます。この構造体は可変であるため、時間、タイムステップ、およびデータはすべて変更可能であり、`SVector` として保存されるデータが効率的である場合があります。

# コンストラクタ

```
KnotPoint{n,m}(v, t, dt)
KnotPoint{n,m}(x, u, t, dt)
KnotPoint{n,m}(n, m, v, t, dt) 
KnotPoint(n, m, v, t, dt)       # KnotPoint{Any,Any} を作成
KnotPoint(x, u, t, dt)
```

最後のメソッドは、`x` と `u` が `StaticVector` でない場合、`KnotPoint{Any,Any}` を作成します。

ベクトル型 `V` は `vectype(z)` を使用して照会できます。
