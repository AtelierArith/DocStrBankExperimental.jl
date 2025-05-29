```
reorganisation_energy(J::AbstractSD)
```

与えられたスペクトル密度 `J` の再編成エネルギーを計算します。すなわち、

$$
\int_0^\infty \frac{J(\omega)}{\omega} \mathrm{d}\omega 
$$

# 引数

  * `J::AbstractSD`: スペクトル密度。

# 戻り値

  * スペクトル密度 `J` の再編成エネルギー。
