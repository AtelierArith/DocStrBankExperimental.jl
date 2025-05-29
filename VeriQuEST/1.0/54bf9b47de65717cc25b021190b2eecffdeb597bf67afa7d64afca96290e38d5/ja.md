```
MBQCOutput(indices)
```

  * グラフへの出力セットを表す構造体で、空であることもあります。

# パラメータ

  * `indices`: 通常の整数（1からNまでの整数）で構成されるタプル型で、グラフの頂点に対応します。

# 例

```
julia> indices = (10,11,12)
julia> mbqc_output = MBQCOutput(indices)
```
