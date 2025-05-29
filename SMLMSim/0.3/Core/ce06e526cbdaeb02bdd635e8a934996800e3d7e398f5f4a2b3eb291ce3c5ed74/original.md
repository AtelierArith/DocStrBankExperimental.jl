```
get_state(ctmc::CTMC, t::AbstractFloat)
```

Get the state of the CTMC at a specific time point.

# Arguments

  * `ctmc::CTMC`: The CTMC to query
  * `t::AbstractFloat`: Time point of interest

# Returns

  * `Int`: State of the chain at time t

# Note

Searches through transition times to find the state active at time t. Returns the state that was entered at the last transition before t.
