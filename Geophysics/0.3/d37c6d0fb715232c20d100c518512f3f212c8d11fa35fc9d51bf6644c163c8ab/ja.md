```
density(h::Real=0,W::Weather=Standard) = density(W(h))
```

気象地点の高度 `h` における単位体積あたりの慣性質量 `ρ` (kg⋅m⁻³ または slugs⋅ft⁻³)。
