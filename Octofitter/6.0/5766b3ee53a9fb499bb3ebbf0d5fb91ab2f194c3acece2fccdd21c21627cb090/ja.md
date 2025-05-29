```
PhotometryLikelihood(
    (band = :Z, phot=15.0, σ_phot=3.),
    (band = :J, phot=13.5, σ_phot=0.5),
    (band = :L, phot=11.0, σ_phot=1.0)
)
```

測定されたフォトメトリーポイントを1つ以上のフィルターバンドでデータ（ここに提供）と比較するための尤度です。`:band`、`:phot`、および `:σ_phot` 列が必要です。Tables.jl 互換のデータソースで提供できます。
