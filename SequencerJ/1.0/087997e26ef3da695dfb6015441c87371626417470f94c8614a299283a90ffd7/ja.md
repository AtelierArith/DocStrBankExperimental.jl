```
EMD(u::AbstractVector{T}, v::AbstractVector{T}) where {T <: Real}
```

与えられた2つのベクトル間の地球移動距離（EMD）、すなわち1-Wasserstein距離を計算します。デフォルトのグリッドを受け入れます。`u`と`v`はグリッド上の重みとして扱われます。デフォルトのグリッドは`u`と`v`の最初の軸に等しいです。

```@example 1
u = rand(10);
u .= u / sum(u);
sum(u)
```

`EMD`は、実行可能な型のDistanciasパッケージの規約を実装しています：

```@example 1
v = rand(10);
v .= v / sum(v);
d = EMD()(u,v)
```
