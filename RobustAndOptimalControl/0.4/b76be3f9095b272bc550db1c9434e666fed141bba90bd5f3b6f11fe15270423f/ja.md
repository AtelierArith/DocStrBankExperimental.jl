```
dare3(P::AbstractStateSpace, Q1::AbstractMatrix, Q2::AbstractMatrix, Q3::AbstractMatrix; full=false)
```

離散時間代数リカッティ方程式を解き、制御差分で拡張された離散LQRコストを求めます。

$$
x^{T} Q_1 x + u^{T} Q_2 u + Δu^{T} Q_3 Δu, \quad
Δu = u(k) - u(k-1)
$$

`full`が`true`の場合、返される行列には状態`u(k-1)`が含まれます。そうでない場合、返される行列は`Q1`と同じサイズになります。
