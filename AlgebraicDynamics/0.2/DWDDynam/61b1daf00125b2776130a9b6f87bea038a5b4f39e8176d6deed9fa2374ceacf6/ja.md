```
euler_approx(m::ContinuousMachine, h::Float)
```

連続マシン `m` をオイラー法を用いてステップサイズ `h` の離散マシンに変換します。もし `m` の動力学が $\dot{u}(t) = f(u(t),x(t),p,t)$ で与えられる場合、新しい離散システムの動力学は更新ルール $u_{n+1} = u_n + h f(u_n, x_n, p, t)$ によって与えられます。
