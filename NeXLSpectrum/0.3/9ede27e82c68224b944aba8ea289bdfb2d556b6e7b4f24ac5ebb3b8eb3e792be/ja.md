```
peaktobackground(ffr::FilterFitResult, backwidth::Float64=10.0)::Float64
```

フィット領域で統合された生のスペクトルと残差スペクトルから決定されたピーク対バックグラウンド比であり、連続体の `backwidth` eV（名目上10 eV）にスケーリングされています。
