```
StateSpaceProblem(css::ContinuousStateSpace, u0::Vector{Float64}, h::Float64, F::Matrix{Float64})
```

Structure containing data for the state-space model

**Constructor**

  * `css`: Continuous-time state space model
  * `u0`: Initial conditions
  * `F`: External force matrix
  * `t`: Time vector

**Fields**

  * `css`: ContinuousStateSpace
  * `F`: External force matrix
  * `u0`: Initial conditions
  * `h`: Time step
