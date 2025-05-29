```
schur_reduce(Π, C, [R])
```

Computes the tuple (S, K, Σ) associated with the following (block) Schur reduction:

```
[C*Π*C'+R C*Π; Π*C' Π] = [0 0; 0 Σ] + [I; K]*(C*Π*C' + R)*[I; K]'
```

In terms of Kalman filtering, Π is the predictive covariance, C the measurement matrix, and R the measurement covariance, then S is the marginal measurement covariance, K is the Kalman gain, and Σ is the filtering covariance.
