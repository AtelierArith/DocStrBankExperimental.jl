```
y = is_ADC_on(x::Sequence)
y = is_ADC_on(x::Sequence, t::Union{Array{Float64,1}, Array{Float64,2}})
```

Tells if the sequence `seq` has elements with ADC active, or active during time `t`.

# Arguments

  * `x`: (`::Sequence`) sequence struct
  * `t`: (`::Union{Array{Float64,1}, Array{Float64,2}}`, `[s]`) time to check

# Returns

  * `y`: (`::Bool`) boolean that tells whether or not the ADC in the sequence is active
