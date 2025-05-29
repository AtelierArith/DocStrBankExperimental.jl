```
function set_limit!(CH::AbstractChart, limit::AbstractLimit)
function set_limit!(CH::AbstractChart, h::Float64)
function set_limit!(CH::MultipleControlChart, h::Vector{Float64})
function set_limit!(CH::MultipleControlChart, h::Float64)
function set_limit!(CH::MultipleControlChart, h::Float64, j::Int)
```

Set the control limit of a control chart.

### Returns

The new control limit.
