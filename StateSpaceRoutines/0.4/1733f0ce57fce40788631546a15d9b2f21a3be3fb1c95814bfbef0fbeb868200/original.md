```
init_stationary_states(T, R, C, Q)
```

Compute the initial state `s_0` and state covariance matrix `P_0` under the stationarity condition:

```
s_0  =  (I - T) \ C
P_0 = reshape(I - kron(T, T)) \ vec(R*Q*R'), Ns, Ns)
```

where:

  * `kron(T, T)` is a matrix of dimension `Ns^2` x `Ns^2`, the Kronecker product of `T`
  * `vec(R*Q*R')` is the `Ns^2` x 1 column vector constructed by stacking the `Ns` columns of `R*Q*R'`

All eigenvalues of `T` are inside the unit circle when the state space model is stationary. When the preceding formula cannot be applied, the initial state vector estimate is set to `C` and its covariance matrix is given by `1e6 * I`.
