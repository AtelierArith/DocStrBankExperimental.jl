```
trees(b::Booster; with_stats=true)
```

`Booster` `b` のモデルのすべての木を [`Node`](@ref) オブジェクトとして返します。この関数の出力は、各々が別々の木の根を表す `Node` の `Vector` です。

`with_stats` が指定されている場合、出力される `Node` オブジェクトには計算された統計 `gain` と `cover` が含まれます。
