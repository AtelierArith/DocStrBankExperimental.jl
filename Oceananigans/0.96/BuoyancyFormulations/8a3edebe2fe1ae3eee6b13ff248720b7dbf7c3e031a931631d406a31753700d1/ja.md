```
SeawaterBuoyancy{FT, EOS, T, S} <: AbstractBuoyancyFormulation{EOS}
```

海水の浮力定式。`T` と `S` は、温度と塩分の両方がアクティブな場合は `nothing` であり、温度または塩分が一定の場合はそれぞれ `FT` 型です。
