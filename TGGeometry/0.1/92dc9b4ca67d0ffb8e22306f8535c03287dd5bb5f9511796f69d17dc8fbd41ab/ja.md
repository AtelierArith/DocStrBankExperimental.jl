```
intersects(geom1, geom2)
```

`geom1` と `geom2` が交差するかどうかを確認します。これは DE-9IM [^de9im] によって定義されています。

具体的には、2つのジオメトリの交差が空の集合にならないことを確認します。

# 引数

  * `geom1`: 最初のジオメトリ。GeoInterface 互換のジオメトリであれば何でも可能です。
  * `geom2`: 2番目のジオメトリ。GeoInterface 互換のジオメトリであれば何でも可能です。

[^de9im]: 2つの平面ジオメトリ間の関係を説明する [次元拡張 9-交差モデル](https://en.wikipedia.org/wiki/DE-9IM)。
