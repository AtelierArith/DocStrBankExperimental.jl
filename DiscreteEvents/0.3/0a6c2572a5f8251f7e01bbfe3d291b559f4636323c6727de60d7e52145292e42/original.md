```
setUnit!(clk::Clock, new::FreeUnits)
```

set a clock to a new time unit in `Unitful`. If necessary convert current clock times to the new unit.

# Arguments

  * `clk::Clock`
  * `new::FreeUnits`: new is one of `ms`, `s`, `minute` or `hr` or another Unitful   `Time` unit.

# Examples

```jldoctest
julia> using DiscreteEvents, Unitful

julia> import Unitful: Time, s, minute, hr

julia> c = Clock(t0=60)     # setup a new clock with t0=60
Clock 1: state=:idle, t=60.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> tau(c)               # current time is 60.0 NoUnits
60.0

julia> setUnit!(c, s)       # set clock unit to Unitful.s
60.0 s

julia> tau(c)               # current time is now 60.0 s
60.0 s

julia> setUnit!(c, minute)  # set clock unit to Unitful.minute
1.0 minute

julia> tau(c)               # current time is now 1.0 minute
1.0 minute

julia> isa(tau(c), Time)
true

julia> uconvert(s, tau(c))  # ... which can be converted to other time units
60.0 s

julia> tau(c).val           # it has a value of 1.0
1.0

julia> c.time               # internal clock time is set to 1.0 (a Float64)
1.0

julia> c.unit               # internal clock unit is set to Unitful.minute
minute
```
