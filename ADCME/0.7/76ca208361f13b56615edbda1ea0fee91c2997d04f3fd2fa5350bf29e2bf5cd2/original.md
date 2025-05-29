```
MCMCSimple(obs::Array{Float64, 1}, h::Function, 
σ::Float64, θ0::Array{Float64,1}, lb::Float64, ub::Float64)
```

A very simple yet useful interface for MCMC simulation in many scientific computing problems. 

  * `obs`: Observations
  * `h`: Forward computation function
  * `σ`: Noise standard deviation for the observed data
  * `ub`, `lb`: upper and lower bound
  * `θ0`: Initial guess

The mathematical model is 

$$
y_{obs} = h(\theta)
$$

and we have a hard constraint `lb\leq \theta \leq ub`. 
