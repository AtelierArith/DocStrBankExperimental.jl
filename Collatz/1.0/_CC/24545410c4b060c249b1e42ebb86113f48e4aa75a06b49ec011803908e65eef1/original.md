Cycle Control: Descriptive flags to indicate when some event occurs in the hailstone sequences, when set to verbose, or stopping time check. A module used to wrap an enum to reference the values as `_CC.ABC` rather than `ABC::CC`

# Examples

```jldoctest
julia> string(_CC.STOPPING_TIME)
"STOPPING_TIME"
julia> string(_CC.TOTAL_STOPPING_TIME)
"TOTAL_STOPPING_TIME"
julia> string(_CC.CYCLE_INIT)
"CYCLE_INIT"
julia> string(_CC.CYCLE_LENGTH)
"CYCLE_LENGTH"
julia> string(_CC.MAX_STOP_OOB)
"MAX_STOP_OOB"
julia> string(_CC.ZERO_STOP)
"ZERO_STOP"
```
