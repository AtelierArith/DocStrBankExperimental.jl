```
koopman_smoother(y, T, R, C, Q, Z, D, E, s_0, P_0, s_pred, P_pred;
    Nt0 = 0)

koopman_smoother(regime_indices, y, Ts, Rs, Cs, Qs, Zs, Ds, Es,
    s_0, P_0, s_pred, P_pred; Nt0 = 0)
```

This is a Kalman smoothing program based on S.J. Koopman's "Disturbance Smoother for State Space Models" (Biometrika, 1993), as specified in Durbin and Koopman's "A Simple and Efficient Simulation Smoother for State Space Time Series Analysis" (Biometrika, 2002).

Unlike other Kalman smoothing programs, there is no need to invert singular matrices using the Moore-Penrose pseudoinverse (`pinv`), which should lead to efficiency gains and fewer inversion problems. Also, the states vector and the corresponding matrices do not need to be augmented to include the shock innovations. Instead they are saved automatically in the `ϵ_smth` matrix.

The state space is given by:

```
s_{t+1} = C + T*s_t + R*ϵ_t    (transition equation)
y_t     = D + Z*s_t + u_t      (measurement equation)

ϵ_t ∼ N(0, Q)
u_t ∼ N(0, E)
Cov(ϵ_t, u_t) = 0
```

### Inputs

  * `y`: `Ny` x `Nt` matrix containing data `y_1, ... , y_T`
  * `s_0`: `Ns` x 1 initial state vector
  * `P_0`: `Ns` x `Ns` initial state covariance matrix
  * `s_pred`: `Ns` x `Nt` matrix of one-step predicted state vectors `s_{t|t-1}` (from the Kalman filter)
  * `P_pred`: `Ns` x `Ns` x `Nt` array of mean squared errors `P_{t|t-1}` of predicted state vectors

**Method 1 only:** state-space system matrices `T`, `R`, `C`, `Q`, `Z`, `D`, `E`. See `?kalman_filter`

**Method 2 only:** `regime_indices` and system matrices for each regime `Ts`, `Rs`, `Cs`, `Qs`, `Zs`, `Ds`, `Es`. See `?kalman_filter`

where:

  * `Nt`: number of periods for which we have data
  * `Ns`: number of states
  * `Ne`: number of shocks
  * `Ny`: number of observables

### Keyword Arguments

  * `Nt0`: if greater than 0, the returned smoothed states and shocks matrices will be shorter by that number of columns (taken from the beginning)

### Outputs

  * `s_smth`: `Ns` x `Nt` matrix of smoothed states `s_{t|T}`
  * `ϵ_smth`: `Ne` x `Nt` matrix of smoothed shocks `ϵ_{t|T}`
