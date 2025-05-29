```
get_pointing_pixels(ss::ScanningStrategy, start, stop)
```

This function will return pointing pixel tod as tuple.     # Arguments     ...     - `ss::ScanningStrategy`: the ScanningStrategy struct.     - `start::Int`: the initial time for pointing calculation.     - `stop::Int`: the finish time for pointing calculation.     ...

````
# Examples
```jldoctest
julia> ss = gen_ScanningStrategy()
julia> pointings = get_pointing_pixels(s, 0, 100)

# Returns
...
- `pointings[1]`: TOD of pixel indicies. shape:(duration*sampling_rate, numOfdet)
- `pointings[2]`: TOD of psi. shape:(duration*sampling_rate, numOfdet)
- `pointings[3]`: Array of time. shape:(duration*sampling_rate)
...
````
