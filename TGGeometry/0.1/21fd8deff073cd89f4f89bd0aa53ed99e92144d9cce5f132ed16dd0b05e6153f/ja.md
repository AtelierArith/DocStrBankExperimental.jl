```
contains(geom1, geom2)
```

`geom1`が`geom2`を完全に含むかどうかを確認します。これはDE-9IM [^de9im]によって定義されています。

これは、`geom2`の境界と内部が完全に`geom1`の内部にあり、`geom1`の外部と交差してはならないことを意味します。

# 引数

  * `geom1`: 最初のジオメトリ。GeoInterface互換のジオメトリであれば何でも可能です。
  * `geom2`: 2番目のジオメトリ。GeoInterface互換のジオメトリであれば何でも可能です。

[^de9im]: 2つの平面ジオメトリ間の関係を説明する[次元拡張9交差モデル](https://en.wikipedia.org/wiki/DE-9IM)。
