```
sdiff(a::T, b::T) where T <: SpiceCell
```

2つの任意のデータ型の集合の対称差を計算して、3番目の集合を形成します。

### 引数

  * `a`: 最初の入力集合
  * `b`: 2番目の入力集合

### 出力

`a` と `b` の対称差を含むセルを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/sdiff_c.html)
