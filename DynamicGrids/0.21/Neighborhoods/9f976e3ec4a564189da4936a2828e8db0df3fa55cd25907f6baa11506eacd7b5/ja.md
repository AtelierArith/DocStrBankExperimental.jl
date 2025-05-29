```
positions(x::Union{Neighborhood,NeighborhoodRule}}, cellindex::Tuple) -> iterable
```

すべてのセルに対して、メイン配列の各インデックスの`Tuple`としてインデックス可能なイテラブルを返します。これは、近隣値を設定するための`SetNeighborhoodRule`や、Aux配列の値を取得するために便利です。
