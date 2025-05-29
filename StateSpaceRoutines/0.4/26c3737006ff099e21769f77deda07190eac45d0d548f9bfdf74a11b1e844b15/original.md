```
hamilton_smoother(y, T, R, C, Q, Z, D, E, s_0, P_0; Nt0 = 0)

hamilton_smoother(regime_indices, y, Ts, Rs, Cs, Qs,
    Zs, Ds, Es, s_0, P_0; Nt0 = 0)
```

This is a Kalman smoothing program based on the treatment in James Hamilton's "Time Series Analysis". Unlike the Koopman smoother, this one does rely on inverting potentially singular matrices using the Moore-Penrose pseudoinverse.

The state space is augmented with shocks (see `?augment_states_with_shocks`), and the augmented state space is Kalman filtered and smoothed. Finally, the smoothed states and shocks are indexed out of the augmented state vectors.

The original state space (before augmenting with shocks) is given by:

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
