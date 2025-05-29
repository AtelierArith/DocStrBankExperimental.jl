```
koopman_disturbance_smoother(y, T, R, Q, Z, D, E, s_pred, P_pred;
    Nt0 = 0, output = [:states, :obs])

koopman_smoother(regime_indices, y, Ts, Rs, Qs, Zs, Ds, Es,
    s_pred, P_pred; Nt0 = 0)
```

This disturbance smoother is intended for use with the state smoother `koopman_smoother` from S.J. Koopman's "Disturbance Smoother for State Space Models" (Biometrika, 1993), as specified in Durbin and Koopman's "A Simple and Efficient Simulation Smoother for State Space Time Series Analysis" (Biometrika, 2002).

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
  * `s_pred`: `Ns` x `Nt` matrix of one-step predicted state vectors `s_{t|t-1}` (from the Kalman filter)
  * `P_pred`: `Ns` x `Ns` x `Nt` array of mean squared errors `P_{t|t-1}` of predicted state vectors

**Method 1 only:** state-space system matrices `T`, `R`, `Q`, `Z`, `D`, `E`. See `?kalman_filter`

**Method 2 only:** `regime_indices` and system matrices for each regime `Ts`, `Rs`, `Qs`, `Zs`, `Ds`, `Es`. See `?kalman_filter`

where:

  * `Nt`: number of periods for which we have data
  * `Ns`: number of states
  * `Ne`: number of shocks
  * `Ny`: number of observables

### Keyword Arguments

  * `Nt0`: if greater than 0, the returned smoothed disturbances and shocks matrices will be shorter by that number of columns (taken from the beginning)
  * `obs_disturbance`: if true, then we return both the transition equation   and measurement equation disturbances. Otherwise, only   the transition equation disturbances are returned.

### Outputs

  * `s_dist`: `Ns` x `Nt` matrix of transition equation disturbances `r_t`
  * `y_dist`: `Ny` x `Nt` matrix of measurement equation disturbances `e_t`
