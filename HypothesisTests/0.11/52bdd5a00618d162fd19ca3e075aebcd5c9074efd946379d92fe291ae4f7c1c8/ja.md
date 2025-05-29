```
confint(x::FisherExactTest; level::Float64=0.95, tail::Symbol=:both, method::Symbol=:central)
```

信頼区間をカバレッジ `level` で計算します。片側区間はフィッシャーの非中心超幾何分布に基づいています。`tail = :both` の場合、実装されている唯一の `method` は中央区間（`:central`）です。

!!! note
    p値が必ずしも単峰性でないため、対応する信頼領域は区間でない可能性があります。


# 参考文献

  * Gibbons, J.D, Pratt, J.W. P値: 解釈と方法論, American Statistican, 29(1):20-25, 1975.
  * Fay, M.P., "フィッシャーの正確な検定またはブレイカーの正確な検定に一致する信頼区間" の補足資料. Biostatistics, Volume 11, Issue 2, 2010年4月1日, ページ 373–374, [link](https://doi.org/10.1093/biostatistics/kxp050)
