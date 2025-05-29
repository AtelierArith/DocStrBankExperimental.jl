```
stdscore(measure::Measurement, expected_value::Real) -> standard_score
```

Gives the standard score between a measure, with uncertainty, and its expected value:

```
(measure.val - expected_value)/measure.err
```
