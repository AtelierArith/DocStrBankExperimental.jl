```
FlexIx{I}(indices)
```

`fi = FlexIx{I}(indices)` の場合:

  * `a[fi]` のインデックス指定は `a[indices]` と同等です;
  * `@set a[fi] = vs` は、`vs` の長さが `indices` と異なっていても機能し、必要に応じて `a` の長さを短縮または延長します。
