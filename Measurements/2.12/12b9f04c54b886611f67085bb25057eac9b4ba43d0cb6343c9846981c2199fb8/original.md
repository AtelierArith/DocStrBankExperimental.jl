```
stdscore(measure_1::Measurement, measure_2::Measurement) -> standard_score
```

Gives the standard score between two measurements (both with uncertainty) computed as the standard score between their difference and 0:

```
stdscore(measure_1 - measure_2, 0)
```
