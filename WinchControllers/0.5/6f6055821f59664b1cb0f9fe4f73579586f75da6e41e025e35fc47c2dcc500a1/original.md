```
mutable struct Mixer_3CH
```

Mix three analog inputs. It selects either input a or input b or input c depending on the values of the digital inputs  and implements soft switching with a blend time `t_blend`. Implements the following block diagram:   ![mixer_3ch](assets/mixer_3ch.png).

## Fields

  * `dt::Float64`
  * `t_blend::Float64`: Default: 1.0
  * `factor_b::Float64`: Default: 0
  * `factor_c::Float64`: Default: 0
  * `select_b::Bool`: Default: false
  * `select_c::Bool`: Default: false

# Example

```julia
using WinchControllers, ControlPlots

TIME = range(0.0, 10, 501)
SIN1 = sin.(TIME * 0.5 * 2pi) * 2
SIN2 = sin.(TIME * 0.25 * 2pi)
NOISE = (rand(501).-0.5) * 2
mix3 = Mixer_3CH(10, 0.25)
out  = zeros(501)

for i in 1:501                   # 10s with dt=0.02
    if i == 150
        select_b(mix3, true)
    elseif i == 300
        select_c(mix3, true)
    elseif i == 450
        select_c(mix3, false)        
    end
    out[i] = calc_output(mix3, SIN1[i], SIN2[i], NOISE[i])
    on_timer(mix3)
end
plot(TIME, out)
```
