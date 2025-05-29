```
DSP.resample(sys::AbstractStateSpace{<:Discrete}, Qd::AbstractMatrix, newh::Real)
```

Change sample time of covariance matrix `Qd` beloning to `sys` to `newh`. This function does not handle the measurement covariance, how to do this depends on context. If the faster sampled signal has the same measurement noise, no change should be made. If the slower sampled signal was downsampled with filtering, the measurement covariance should be increased if the system is changed to a faster sample rate. To maintain the frequency response of the system, the measurement covariance should be modified accordinly.

# Arguments:

  * `sys`: A discrete-time system that has dynamics noise covariance matric `Qd`.
  * `Qd`: Covariance matrix of dynamics noise.
  * `newh`: The new sample time.
