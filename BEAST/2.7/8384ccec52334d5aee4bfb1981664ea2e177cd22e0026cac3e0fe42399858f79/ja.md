```
laplace_to_z(rho, n, N, dt, A, b)
```

与えられたバターチャート (A,b,c) と時間ステップ dt に対して、変数 z = rho*exp(2*im*pi*n/N) に対応する複素行列値ラプラス変数 s を返します。
