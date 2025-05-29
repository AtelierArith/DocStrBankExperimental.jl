```
get_pointings_tuple(ss::ScanningStrategy_ThetaPhi, start, stop)
```

This function will return pointing tod as tuple.     # Arguments     ...     - `ss::ScanningStrategy_ThetaPhi`: the ScanningStrategy_ThetaPhi struct.     - `start::Int`: the initial time for pointing calculation.     - `stop::Int`: the finish time for pointing calculation.     ...

````
# Examples
```jldoctest
julia> ss = gen_ScanningStrategy_ThetaPhi()
julia> pointings = get_pointings_tuple(s, 0, 100)

# Returns
...
- `pointings[1]`: TOD of theta. shape:(duration*sampling_rate, numOfdet)
- `pointings[2]`: TOD of phi. shape:(duration*sampling_rate, numOfdet)
- `pointings[3]`: TOD of psi. shape:(duration*sampling_rate, numOfdet)
- `pointings[4]`: Array of time. shape:(duration*sampling_rate)
...
````
