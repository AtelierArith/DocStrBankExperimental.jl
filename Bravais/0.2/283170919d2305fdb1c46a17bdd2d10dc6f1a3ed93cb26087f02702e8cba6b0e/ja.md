```
volume(Vs::AbstractBasis)
```

基底 `Vs::AbstractBasis{D}` に関連付けられた単位セルの体積 $V$ を返します。

体積は $V = \sqrt{\mathrm{det}\mathbf{G}}$ として計算され、ここで $\mathbf{G}$ は `Vs` のメトリック行列を示します（国際結晶学表、ボリューム A、セクション 5.2.2.3 を参照）。

[`metricmatrix`](@ref) も参照してください。
