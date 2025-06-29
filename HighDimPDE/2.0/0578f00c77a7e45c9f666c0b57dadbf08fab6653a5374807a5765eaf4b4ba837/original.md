```julia
DeepBSDE(u0,σᵀ∇u;opt=Flux.Optimise.Adam(0.1))
```

[DeepBSDE algorithm](https://arxiv.org/abs/1707.02568), from J. Han, A. Jentzen and Weinan E. 

## Arguments

  * `u0`: a Flux.jl `Chain` with a d-dimensional input and a 1-dimensional output for the solytion guess.
  * `σᵀ∇u`: a Flux.jl `Chain` for the BSDE value guess.
  * `opt`: the optimization algorithm to be used to optimize the neural networks. Defaults to `Flux.Optimise.Adam(0.1)`.

## Example

Black-Scholes-Barenblatt equation

```julia
d = 30 # number of dimensions
x0 = repeat([1.0f0, 0.5f0], div(d,2))
tspan = (0.0f0,1.0f0)
dt = 0.2
m = 30 # number of trajectories (batch size)

r = 0.05f0
sigma = 0.4f0
f(X,u,σᵀ∇u,p,t) = r * (u - sum(X.*σᵀ∇u))
g(X) = sum(X.^2)
μ_f(X,p,t) = zero(X) #Vector d x 1
σ_f(X,p,t) = Diagonal(sigma*X) #Matrix d x d
prob = PIDEProblem(μ_f, σ_f, x0, tspan, g, f)

hls  = 10 + d #hidden layer size
opt = Flux.Optimise.Adam(0.001)
u0 = Flux.Chain(Dense(d,hls,relu),
                Dense(hls,hls,relu),
                Dense(hls,1))
σᵀ∇u = Flux.Chain(Dense(d+1,hls,relu),
                  Dense(hls,hls,relu),
                  Dense(hls,hls,relu),
                  Dense(hls,d))
pdealg = DeepBSDE(u0, σᵀ∇u, opt=opt)

solve(prob, 
    pdealg, 
    EM(), 
    verbose=true, 
    maxiters=150, 
    trajectories=m, 
    sdealg=StochasticDiffEq., 
    dt=dt, 
    pabstol = 1f-6)
```
