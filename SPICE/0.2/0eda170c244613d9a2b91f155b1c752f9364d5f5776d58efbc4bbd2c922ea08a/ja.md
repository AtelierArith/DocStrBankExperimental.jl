```
getelm(frstyr, lines)
```

与えられた2行要素セットの「lines」を解析し、SPICEソフトウェアで使用するのに適した単位の要素を返します。

### 引数

  * `frstyr`: 表現可能な最も古い2行要素の年
  * `lines`: 2行要素を含む「行」のペア

### 出力

  * `epoch`: J2000からの秒数で表された要素のエポック
  * `elems`: SPICE単位に変換された要素

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getelm_c.html)

```
