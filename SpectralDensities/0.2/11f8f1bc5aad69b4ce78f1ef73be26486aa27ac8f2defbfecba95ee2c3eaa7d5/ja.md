```
struct PolySD <: AbstractSD
```

PolySDは多項式スペクトル密度を表します。これは、結合の強さを表す振幅`α`と多項式の次数`n`によって特徴付けられます。すなわち

$$
J(\omega) = \alpha\omega^n
$$

# フィールド

  * `α::Float64`: 結合の強さを示す振幅`α`。
  * `n::Int`: 多項式の次数。
