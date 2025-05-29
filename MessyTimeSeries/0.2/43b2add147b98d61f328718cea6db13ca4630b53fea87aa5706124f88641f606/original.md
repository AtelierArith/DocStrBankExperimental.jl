```
KalmanSettings(...)
```

Define an immutable structure that includes all the Kalman filter and smoother inputs.

# Model

The state space model used below is,

$Y_{t} = B*X_{t} + e_{t}$

$X_{t} = C*X_{t-1} + D*U_{t}$

where $e_{t} \sim N(0_{nx1}, R)$ and $U_{t} \sim N(0_{mx1}, Q)$.

# Fields

  * `Y`: Observed measurements (`nxT`)
  * `B`: Measurement equations' coefficients
  * `R`: Covariance matrix of the measurement equations' error terms
  * `C`: Transition equations' coefficients
  * `D`: Transition equations' coefficients associated to the error terms
  * `Q`: Covariance matrix of the transition equations' error terms
  * `X0`: Mean vector for the states at time $t=0$
  * `P0`: Covariance matrix for the states at time $t=0$
  * `DQD`: Covariance matrix of $D*U_{t}$ (i.e., $D*Q*D'$)
  * `m`: Number of latent states
  * `compute_loglik`: Boolean (`true` for computing the loglikelihood in the Kalman filter)
  * `store_history`: Boolean (`true` to store the history of the filter and smoother)
