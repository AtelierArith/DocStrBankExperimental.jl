```
gfudb!(udfuns, udfunb, step, cnfine, result)
```

ユーザー定義のブール量に対してGF検索を実行します。

### 引数

  * `udfuns`: `et`に対応するスカラー量を計算するルーチンの名前、例: `f(et) = ...`
  * `udfunb`: `et`に対応するブール値を返すルーチンの名前、例: `g(f, et) = ...`
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `cnfine`: 検索が制限されるウィンドウ
  * `result`: 結果を含むウィンドウ

### 出力

`result`を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfudb_c.html)
