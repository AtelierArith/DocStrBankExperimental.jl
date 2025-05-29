```
lqr3(P::AbstractStateSpace, Q1::AbstractMatrix, Q2::AbstractMatrix, Q3::AbstractMatrix)
```

制御差分で拡張された離散LQRコスト関数のフィードバックゲインを計算します

$$
x^{T} Q_1 x + u^{T} Q_2 u + Δu^{T} Q_3 Δu, \quad
Δu = u(k) - u(k-1)
$$
