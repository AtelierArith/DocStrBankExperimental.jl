```
WCADivision{P<:Potential, T, UC}
```

フィールド

  * `potential::Potential`
  * `cutoff` : ($r_{c}$)
  * `U_c` : $U(r=r_c)$

カットオフポイントで`potential`をWCA分割ルールを使用して分割します。これは次のことを意味します。

$$
u(r) = u_{SR}(r) + U_{LR}(r),
$$

ここで、$U_{LR}(r) = u(r)$は$r > r_{c}$の場合、$U(r_{c})$は$r < r_{c}$の場合、$USR(r) = 0$は$r > r_{c}$の場合、$U(r) - U(r_{c})$は$r < r_{c}$の場合です。
