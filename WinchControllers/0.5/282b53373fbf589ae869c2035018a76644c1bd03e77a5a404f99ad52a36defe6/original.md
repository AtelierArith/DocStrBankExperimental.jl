```
mutable struct Mixer_2CH
```

Mix two analog inputs.  It selects either input a or input b depending on the value of the digital input and implements  soft switching with a blend time `t_blend`. Implements the following block diagram: ![mixer_2ch](assets/mixer_2ch.png).

## Fields

  * `dt::Float64`
  * `t_blend::Float64`: Default: 1.0
  * `factor_b::Float64`: Default: 0
  * `select_b::Bool`: Default: false

# Example

```julia
using WinchControllers, Test

m2 = Mixer_2CH(0.2, 1.0) # dt=0.2s, t_blend = 1.0s
x = ones(10)
y = 2*x
out = zeros(10)
for i in 1:length(x)
    in1=x[i]
    in2=y[i]
    out[i] = calc_output(m2, x[i], y[i])
    select_b(m2, i > 2)
    on_timer(m2)
end
@test all(out .≈ [1.0, 1.0, 1.0, 1.2, 1.4, 1.6, 1.8, 2.0, 2.0, 2.0])
```
