```
betaU_SW(temperature::T_num, lambda_range::T_num, k::T_num) where {T_num<:AbstractFloat}
```

Auxiliary function that computes the Fourier Transform of the attractive part of a Square-Well (SW) potential, multiplied by β = 1/(k*B T*abs). The result is β * u*attr*SW_tilde(k).

# Arguments

  * `temperature::T_num`: Dimensionless temperature (often k*B * T*abs / ε, where ε is well depth).
  * `lambda_range::T_num`: Range of the square well in terms of the hard-sphere diameter σ (i.e., λ*σ).
  * `k::T_num`: Dimensionless wave vector (k = q*σ).

# Returns

  * `T_num`: The value of β * u*attr*SW_tilde(k).
