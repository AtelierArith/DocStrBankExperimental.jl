```
durbin_koopman_smoother(y, T, R, C, Q, Z, D, E, s_0, P_0;
    Nt0 = 0, draw_states = true)

durbin_koopman_smoother(regime_indices, y, Ts, Rs, Cs, Qs,
    Zs, Ds, Es, s_0, P_0; Nt0 = 0, draw_states = true)
```

This program is a simulation smoother based on Durbin and Koopman's "A Simple and Efficient Simulation Smoother for State Space Time Series Analysis" (Biometrika, 2002).

Unlike other simulation smoothers (for example, that of Carter and Kohn, 1994), this method does not require separate draws for each period, draws of the state vectors, or even draws from a conditional distribution. Instead, vectors of shocks are drawn from the unconditional distribution of shocks, which is then corrected (via a Kalman smoothing step), to yield a draw of shocks conditional on the data. This is then used to generate a draw of states conditional on the data. Drawing the states in this way is much more efficient than other methods, as it avoids the need for multiple draws of state vectors (requiring singular value decompositions), as well as inverting state covariance matrices (requiring the use of the computationally intensive and relatively erratic Moore-Penrose pseudoinverse).

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
  * `pred`: `Ns` x `Nt` matrix of one-step predicted state vectors `s_{t|t-1}` (from the Kalman filter)
  * `vpred`: `Ns` x `Ns` x `Nt` array of mean squared errors `P_{t|t-1}` of predicted state vectors

**Method 1 only:** state-space system matrices `T`, `R`, `C`, `Q`, `Z`, `D`, `E`. See `?kalman_filter`

**Method 2 only:** `regime_indices` and system matrices for each regime `Ts`, `Rs`, `Cs`, `Qs`, `Zs`, `Ds`, `Es`. See `?kalman_filter`

where:

  * `Nt`: number of periods for which we have data
  * `Ns`: number of states
  * `Ne`: number of shocks
  * `Ny`: number of observables

### Keyword Arguments

  * `Nt0`: if greater than 0, the returned smoothed states and shocks matrices will be shorter by that number of columns (taken from the beginning)
  * `draw_states`: indicates whether to draw smoothed states from the distribution `N(s_{t|T}, P_{t|T})` or to use the mean `s_{t|T}` (reducing to the Koopman smoother)

### Outputs

  * `s_smth`: `Ns` x `Nt` matrix of smoothed states `s_{t|T}`
  * `ϵ_smth`: `Ne` x `Nt` matrix of smoothed shocks `ϵ_{t|T}`
