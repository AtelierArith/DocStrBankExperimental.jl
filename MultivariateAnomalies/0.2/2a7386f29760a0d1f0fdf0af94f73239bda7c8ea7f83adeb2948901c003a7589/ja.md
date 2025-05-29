```
EWMA(dat,  λ)
```

指数加重移動平均（EWMA）を、`dat`の最初の次元に沿って、0（完全加重）から1（無加重）までの加重パラメータ`λ`を用いて計算します。N次元配列をサポートしています。

Lowry, C. A., & Woodall, W. H. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34, 46–53.

# 例

```
julia> dc = rand(100,3,2)
julia> ewma_dc = EWMA(dc, 0.1)
```
