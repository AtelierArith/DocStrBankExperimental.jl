```
diff(a::T, b::T) where T <: SpiceCell
```

2つの任意のデータ型のセットの差を計算して、3番目のセットを形成します。

### 引数

  * `a`: 最初の入力セット
  * `b`: 2番目の入力セット

### 出力

`a`と`b`の差を含むセルを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/diff_c.html)
