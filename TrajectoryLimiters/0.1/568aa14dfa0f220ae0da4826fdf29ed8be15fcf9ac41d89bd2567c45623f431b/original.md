```
limiter = TrajectoryLimiter(Ts, ẋM, ẍM)
```

Create a trajectory limiter that can be called like so

```julia
rlim = limiter(state, r::Number)
# or
X, Ẋ, Ẍ = limiter(state, R::Vector)
# or 
X, Ẋ, Ẍ = limiter(R::Vector) # Uses a zero initial state
```
