```
NearestNeighborCluster <: NeutralLandscapeMaker

NearestNeighborCluster(; p=0.5, n=:rook)
NearestNeighborCluster(p, [n=:rook])
```

0-1の値を持つランダムクラスタ最近接隣接中立景観モデルを作成します。`p`は元のクラスタの密度を設定し、`n`はクラスタリングのための近隣を設定します（近隣オプションについては`?label`を参照してください）。
