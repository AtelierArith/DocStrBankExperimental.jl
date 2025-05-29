```
era(YY::AbstractArray{<:Any, 3}, Ts, nx::Int, m::Int = 2nx, n::Int = 2nx)
```

Eigenvalue realization algorithm. The algorithm returns a statespace model.

# Arguments:

  * `YY`: Markov parameters (impulse response) size `ny × nu × n_time`
  * `Ts`: Sample time
  * `nx`: Model order
  * `m`: Number of rows in Hankel matrix
  * `n`: Number of columns in Hankel matrix
