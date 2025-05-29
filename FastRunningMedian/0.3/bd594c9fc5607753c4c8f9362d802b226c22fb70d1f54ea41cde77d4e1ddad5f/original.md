```
running_median(input, window_length, tapering=:symmetric; kwargs...) -> output
```

Run a median filter of `window_length` over the input array and return the result. 

If the input array is multidimensional, the median will be run only over the first dimension, i.e. over all columns indepedently.

## Taperings

The tapering decides the behaviour at the ends of the input. The available taperings are:

  * `:symmteric` or `:sym`: Ensure that the window is symmetric around each point of the output array by always growing or shrinking the window by 2. The output has the same length as the input if `window_length` is odd. If `window_length` is even, the output has one element less.
  * `:asymmetric` or `:asym`: Always adds or removes one element when calculating the next output value. Creates asymmetric windowing at the edges of the array. If the input is N long, the output is N+window_length-1 elements long.
  * `:asymmetric_truncated` or `:asym_trunc`: The same as asymmetric, but truncated at beginning and end to match the length of `:symmetric`.
  * `:none` or `:no`: No tapering towards the ends. If the input has N elements, the output is only N-window_length+1 long. Equivalent to "roll" from [RollingFunctions](https://github.com/JeffreySarnoff/RollingFunctions.jl).
  * `:beginning_only` or `:start`: At the beginning, always grow the window by one but do not taper the end. This is equivalent to asymmetric but truncated at the end such that the output length matches the input length. Equivalent to "run" from [RollingFunctions](https://github.com/JeffreySarnoff/RollingFunctions.jl).

If you choose an even `window_length`, the elements of the output array lie in the middle between the input elements on a continuous underlying axis. 

With the exception of `:beginning_only`, all taperings are mirror symmetric with respect to the middle of the input array.

## Keyword Arguments

  * `nan=:include`: By default, NaN values in the window will turn the median NaN as well. Use `nan = :ignore` to ignore NaN values and calculate the median over the remaining values in the window. If there are only NaNs in the window, the median will be NaN regardless.
  * `output_eltype=Float64`: Element type of the output array. The output element type should allow converting from Float64 and the input element type. The exception is odd window lengths with taperings `:no` or `:sym`, in which case the output element type only has to allow converting from the input element type.

## Performance

The underlying algorithm should scale as O(N log w) with the input length N and the window_length w. 
