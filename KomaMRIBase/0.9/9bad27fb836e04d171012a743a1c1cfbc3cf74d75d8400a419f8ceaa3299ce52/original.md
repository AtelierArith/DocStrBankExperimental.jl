```
y = is_RF_on(x::Sequence)
y = is_RF_on(x::Sequence, t::Vector{Float64})
```

Tells if the sequence `seq` has elements with RF active, or active during time `t`.

# Arguments

  * `x`: (`::Sequence`) Sequence struct
  * `t`: (`::Vector{Float64}`, `[s]`) time to check

# Returns

  * `y`: (`::Bool`) boolean that tells whether or not the RF in the sequence is active
