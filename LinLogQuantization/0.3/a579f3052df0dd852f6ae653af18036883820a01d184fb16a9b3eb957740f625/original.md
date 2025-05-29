```
LinQuantArray(TInteger, A; dims, extrema=nothing)
```

Linear quantization independently for every element along dimension`dims` in array `A`.

# Arguments

  * `TInteger`: the type of the quantised array
  * `A`: the array to quantise
  * `dims`: the dimension along which to quantise
  * `extrema`: the minimum and maximum of the range, defaults to `nothing`.

# Returns

  * a Vector{LinQuantArray} with the quantised array and the minimum and maximum of the original range.
