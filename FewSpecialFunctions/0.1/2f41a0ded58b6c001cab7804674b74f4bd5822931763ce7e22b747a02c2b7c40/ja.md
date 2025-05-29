```
debye_function(n::Float64, β::Float64, x::Float64; 
              tol=1e-35, max_terms=2000) -> Float64
```

パラメータ `n`、`β`、および `x` を用いて一般化されたデバイ関数を計算します。

参考文献:

  * [デバイ関数](https://en.wikipedia.org/wiki/Debye_function)
  * [論文](https://doi.org/10.1007/s10765-007-0256-1)
