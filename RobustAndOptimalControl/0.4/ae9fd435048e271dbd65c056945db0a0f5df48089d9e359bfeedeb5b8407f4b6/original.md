```
lqr3(P::AbstractStateSpace, Q1::AbstractMatrix, Q2::AbstractMatrix, Q3::AbstractMatrix)
```

Calculate the feedback gain of the discrete LQR cost function augmented with control differences

$$
x^{T} Q_1 x + u^{T} Q_2 u + Δu^{T} Q_3 Δu, \quad
Δu = u(k) - u(k-1)
$$
