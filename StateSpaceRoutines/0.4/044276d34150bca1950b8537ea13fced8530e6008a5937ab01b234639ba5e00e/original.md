```
kalman_filter(y, T, R, C, Q, Z, D, E, s_0 = AbstractVector(), P_0 = Matrix();
    outputs = [:loglh, :pred, :filt], Nt0 = 0)

kalman_filter(regime_indices, y, Ts, Rs, Cs, Qs, Zs, Ds, Es,
    s_0 = AbstractVector(), P_0 = Matrix(); outputs = [:loglh, :pred, :filt],
    Nt0 = 0)
```

This function implements the Kalman filter for the following state-space model:

```
s_{t+1} = C + T*s_t + R*ϵ_t    (transition equation)
y_t     = D + Z*s_t + u_t      (measurement equation)

ϵ_t ∼ N(0, Q)
u_t ∼ N(0, E)
Cov(ϵ_t, u_t) = 0
```

### Inputs

  * `y`: `Ny` x `Nt` matrix containing data `y_1, ... , y_T`
  * `s_0`: optional `Ns` x 1 initial state vector
  * `P_0`: optional `Ns` x `Ns` initial state covariance matrix

**Method 1 only:**

  * `T`: `Ns` x `Ns` state transition matrix
  * `R`: `Ns` x `Ne` matrix in the transition equation mapping shocks to states
  * `C`: `Ns` x 1 constant vector in the transition equation
  * `Q`: `Ne` x `Ne` matrix of shock covariances
  * `Z`: `Ny` x `Ns` matrix in the measurement equation mapping states to observables
  * `D`: `Ny` x 1 constant vector in the measurement equation
  * `E`: `Ny` x `Ny` matrix of measurement error covariances

**Method 2 only:**

  * `regime_indices`: `AbstractVector{UnitRange{Int}}` of length `n_regimes`, where `regime_indices[i]` indicates the time periods `t` in regime `i`
  * `Ts`: `AbstractVector{Matrix{S}}` of `T` matrices for each regime
  * `Rs`
  * `Cs`
  * `Qs`
  * `Zs`
  * `Ds`
  * `Es`

where:

  * `Nt`: number of time periods for which we have data
  * `Ns`: number of states
  * `Ne`: number of shocks
  * `Ny`: number of observables

### Keyword Arguments

  * `outputs`: some subset of `[:loglh, :pred, :filt]` specifying which outputs to compute and return. There will always be the same number of return values, but, for example, `s_pred` and `P_pred` will be returned as empty arrays if `:pred` is not in `outputs`
  * `Nt0`: number of presample periods to omit from all return values

### Outputs

  * `loglh`: length `Nt` vector of conditional log-likelihoods P(y*t | y*{1:t-1})
  * `s_pred`: `Ns` x `Nt` matrix of one-step predicted state vectors s_{t|t-1}
  * `P_pred`: `Ns` x `Ns` x `Nt` array of mean squared errors P_{t|t-1} of predicted state vectors
  * `s_filt`: `Ns` x `Nt` matrix of filtered state vectors s_{t|t}
  * `P_filt`: `Ns` x `Ns` x `Nt` matrix containing mean squared errors P_{t|t} of filtered state vectors
  * `s_0`: `Ns` x 1 initial state vector. This may have been reassigned to the last presample state vector if `Nt0 > 0`
  * `P_0`: `Ns` x `Ns` initial state covariance matrix. This may have been reassigned to the last presample state covariance if `Nt0 > 0`
  * `s_T`: `Ns` x 1 final filtered state `s_{T|T}`
  * `P_T`: `Ns` x `Ns` final filtered state covariance matrix `P_{T|T}`

### Notes

When `s_0` and `P_0` are omitted, they are computed using `init_stationary_states`.
