```
FrequencySplit([s, ] f::Real) <: Decomposition
```

[`Fourier`](@ref) メソッドに似ていますが、ここでの「残差」信号は `s` の中で周波数が `f` より高い部分であり、「季節的」部分は周波数が `≤ f` の部分です。
