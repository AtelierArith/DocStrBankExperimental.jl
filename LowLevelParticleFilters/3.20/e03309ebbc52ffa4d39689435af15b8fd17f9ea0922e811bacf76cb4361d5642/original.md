```
SqKalmanFilter(A,B,C,D,R1,R2,d0=MvNormal(R1); p = NullParameters(), α=1)
```

A standard Kalman filter on square-root form. This filter may have better numerical performance when the covariance matrices are ill-conditioned.

The matrices `A,B,C,D` define the dynamics

```
x' = Ax + Bu + w
y  = Cx + Du + e
```

where `w ~ N(0, R1)`, `e ~ N(0, R2)` and `x(0) ~ d0`

The matrices can be time varying such that, e.g., `A[:, :, t]` contains the $A$ matrix at time index `t`. They can also be given as functions on the form

```
Afun(x, u, p, t) -> A
```

The internal fields storing covariance matrices are for this filter storing the upper-triangular Cholesky factor.

α is an optional "forgetting factor", if this is set to a value > 1, such as 1.01-1.2, the filter will, in addition to the covariance inflation due to $R_1$, exhibit "exponential forgetting" similar to a [Recursive Least-Squares (RLS) estimator](https://en.wikipedia.org/wiki/Recursive_least_squares_filter). It is thus possible to get a RLS-like algorithm by setting $R_1=0, R_2 = 1/α$ and $α > 1$ ($α$ is the inverse of the traditional RLS parameter $α = 1/λ$). The form of the covariance update is

$$
R(t+1|t) = α AR(t)A^T + R_1
$$

Ref: "A Square-Root Kalman Filter Using Only QR Decompositions", Kevin Tracy https://arxiv.org/abs/2208.06452
