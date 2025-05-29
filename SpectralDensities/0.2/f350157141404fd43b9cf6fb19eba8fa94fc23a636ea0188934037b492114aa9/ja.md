```
struct OhmicSD <: AbstractSD
```

OhmicSDはオーム的スペクトル密度を表します。これは、オーム結合の強さを表す振幅`α`によって特徴付けられます。すなわち、

$$
J(\omega) = \alpha\omega
$$

# フィールド

  * `α::Float64`: オーム結合の強さを示す振幅`α`。
