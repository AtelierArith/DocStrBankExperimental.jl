```
rowsclass(zep::Zeppelin, classname::AbstractString; shuffle=false, n=1000000)
```

指定された `classname` に関連付けられた行インデックスを返します。 `shuffle` が true の場合、行インデックスはシャッフルされ、ランダム化された n を取り出してプロットやその他の用途に使用できます。

例:

```
# "Calcite" 粒子のランダム化された選択をプロットする
plot(zep, rowsclass(zep, "Calcite", shuffle=true, n=10), xmax=8.0e3)
```
