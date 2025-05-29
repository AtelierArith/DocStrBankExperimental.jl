```
reflection_coef(bc::AbstractAcousticBoundary, frequency, θ)
reflection_coef(bc::AbstractAcousticBoundary, frequency, θ, ρ, c)
```

流体-流体境界のタイプ `bc` における入射角 `θ` と `frequency` での複素反射係数を計算します。水中の密度と音速はそれぞれ `ρ` と `c` で与えられます。
