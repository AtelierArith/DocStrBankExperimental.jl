```
euler_approx(r::ContinuousResourceSharer, h::Float)
```

連続リソースシェアラー `r` を、ステップサイズ `h` を用いてオイラー法により離散リソースシェアラーに変換します。`r` の動力学が $\dot{u}(t) = f(u(t),p,t)$ で与えられる場合、新しい離散システムの動力学は更新ルール $u_{n+1} = u_n + h f(u_n, p, t)$ によって与えられます。
