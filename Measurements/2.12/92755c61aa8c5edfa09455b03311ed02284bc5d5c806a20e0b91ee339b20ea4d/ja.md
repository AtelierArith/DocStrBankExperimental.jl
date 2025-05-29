```
stdscore(measure::Measurement, expected_value::Real) -> standard_score
```

測定値とその期待値との間の標準スコアを返します（不確実性を含む）：

```
(measure.val - expected_value)/measure.err
```
