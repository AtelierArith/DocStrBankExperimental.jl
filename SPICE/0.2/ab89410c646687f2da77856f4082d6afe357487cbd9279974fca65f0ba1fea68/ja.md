```
set(a::T, b::T) where T <: SpiceCell
```

与えられた関係演算子を使用して、任意のデータ型の2つのセットを比較します。

### 引数

  * `a`: 最初のセット
  * `op`: 比較演算子
  * `b`: 2番目のセット

### 出力

比較の結果を返します: `a (op) b`。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/set_c.html)
