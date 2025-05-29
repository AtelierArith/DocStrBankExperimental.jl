```
dare3(P::AbstractStateSpace, Q1::AbstractMatrix, Q2::AbstractMatrix, Q3::AbstractMatrix; full=false)
```

Solve the discrete-time algebraic Riccati equation for a discrete LQR cost augmented with control differences

$$
x^{T} Q_1 x + u^{T} Q_2 u + Δu^{T} Q_3 Δu, \quad
Δu = u(k) - u(k-1)
$$

If `full`, the returned matrix will include the state `u(k-1)`, otherwise the returned matrix will be of the same size as `Q1`.
