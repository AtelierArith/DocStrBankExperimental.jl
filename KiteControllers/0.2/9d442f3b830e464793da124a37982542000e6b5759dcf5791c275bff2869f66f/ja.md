```
on_est_sysstate(fpc, phi, beta, psi, chi, omega, v_a; u_d=nothing, u_d_prime=nothing)
```

パラメータ:

  * phi:      ラジアンでの凧の位置の方位角
  * beta:     ラジアンでの凧の位置の仰角
  * psi:      ラジアンでの凧の見出し
  * chi:      ラジアンでの凧のコース
  * omega:    単位球上の凧の角速度（度/s）???
  * u_d:      デパワー設定             [0..1]
  * u*d*prime 正規化されたデパワー設定  [0..1]

u*d または u*d_prime のいずれかを提供する必要があります。
