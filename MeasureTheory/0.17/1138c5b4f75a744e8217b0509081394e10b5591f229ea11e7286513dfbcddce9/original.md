```
@half dist([paramnames])
```

Starting from a symmetric univariate measure `dist ≪ Lebesgue(ℝ)`, create a new measure `Halfdist ≪ Lebesgue(ℝ₊)`. For example,     @half Normal() creates `HalfNormal()`, and      @half StudentT(ν) creates `HalfStudentT(ν)`.
