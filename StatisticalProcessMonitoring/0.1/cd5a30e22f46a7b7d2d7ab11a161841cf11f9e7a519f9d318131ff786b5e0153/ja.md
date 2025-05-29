```
ALT{M}
```

分散共分散行列の変化を監視するための一般化尤度比統計量。

### フィールド

  * `value::Float64`: 統計量の値で、初期値は0.0。
  * `Ω::M`: 制御内プロセスの精度行列。
  * `detΣ::Float64`: 制御内プロセスの分散の行列式。

### 参考文献

Alt, F. A. (1984). Multivariate quality control. In N. L. Johnson, S. Kotz, & C. R. Read (Eds.), The encyclopedia of statistical sciences (Vol. 6, pp. 110-122). Wiley.
