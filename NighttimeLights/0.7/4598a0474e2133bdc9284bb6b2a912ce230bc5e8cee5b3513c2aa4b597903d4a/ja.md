na_recode関数はデータキューブにも適用できます。

```julia
na_recode(radiance_datacube, ncfobs_datacube)
```

雲のない観測数が0である場合、放射は欠損としてマークされます。
