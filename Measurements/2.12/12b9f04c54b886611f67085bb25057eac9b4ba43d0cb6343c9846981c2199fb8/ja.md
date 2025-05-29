```
stdscore(measure_1::Measurement, measure_2::Measurement) -> standard_score
```

2つの測定値（どちらも不確かさを持つ）間の標準スコアを返します。これは、差と0との間の標準スコアとして計算されます：

```
stdscore(measure_1 - measure_2, 0)
```
