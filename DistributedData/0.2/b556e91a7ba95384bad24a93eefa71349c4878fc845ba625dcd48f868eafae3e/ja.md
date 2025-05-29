```
dstat(dInfo::Dinfo, columns::Vector{Int})::Tuple{Vector{Float64}, Vector{Float64}}
```

データセットの列の平均と標準偏差を計算します。`columns`内の平均のベクトルと対応する標準偏差のベクトルを含むタプルを返します。
