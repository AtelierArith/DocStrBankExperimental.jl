```
disjoint(geom1, geom2)
```

`geom1` と `geom2` が DE-9IM [^de9im] によって定義されるように、互いに完全に非交差し、分離しているかどうかを確認します。

# 引数

  * `geom1`: 最初のジオメトリ。任意の GeoInterface 互換ジオメトリである可能性があります。
  * `geom2`: 2 番目のジオメトリ。任意の GeoInterface 互換ジオメトリである可能性があります。

[^de9im]: 2 つの平面ジオメトリ間の関係を説明する [次元拡張 9 交差モデル](https://en.wikipedia.org/wiki/DE-9IM)。
