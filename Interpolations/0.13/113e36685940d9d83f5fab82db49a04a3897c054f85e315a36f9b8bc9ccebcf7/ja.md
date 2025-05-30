```
itp = interpolate((nodes1, nodes2, ...), A, interpmode)
```

与えられた `nodes` によって指定された非一様だが矩形のグリッド上で配列 `A` を補間し、`interpmode` によって決定されるモードで行います。

`interpmode` は次のいずれかである可能性があります。

  * `NoInterp()`
  * `Gridded(Constant())`
  * `Gridded(Linear())`

異なる補間スキームを各軸に沿って使用したい場合は、そのような値のタプルであることもできます。
