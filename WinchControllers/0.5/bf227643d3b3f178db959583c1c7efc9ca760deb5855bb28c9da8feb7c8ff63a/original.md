```
mutable struct RateLimiter
```

Limit the rate of change of the output signal (return value of `calc_output`) to ± limit. Unit of limit: 1/s.

## Fields

  * `dt::Float64`: Default: 0.05
  * `limit::Float64`: Default: 1
  * `output::Float64`: Default: 0
  * `last_output::Float64`: Default: 0

# Example

```julia
using WinchControllers, ControlPlots
rl = RateLimiter(1.0, 0.8)
input =  [0,0,1,2,3,3,3,3,3,2,1,0,0,0,0,0]
out = zeros(16)
for i in 1:16
    out[i] = calc_output(rl, input[i])
    on_timer(rl)
end
plot(1:16, [input, out]; labels=["input", "output"])
```

![rate_limiter](assets/rate_limiter.png).
