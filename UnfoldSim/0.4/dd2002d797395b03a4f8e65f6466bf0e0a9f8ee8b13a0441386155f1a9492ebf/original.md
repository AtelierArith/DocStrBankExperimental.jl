```
pad_array(arr::Vector, len::Int, val)    
pad_array(arr::Vector, len::Tuple, val)
```

Pads the input array `arr` with a specified value `val` either before or after the existing elements, based on the sign of `len`.

# Arguments

  * `arr::Vector`: The input array to be padded.
  * `len::Union{Int, Tuple}`: The number of times that `val` should be added.   If `len` is negative, the values are added before the existing array. Otherwise, they are added after the existing array.   If `len` is a tuple, `pad_array` is called twice which enables padding the array before and after in one function call.
  * `val`: The value to be used for padding.

# Returns

  * `Vector`: Padded vector with the new length `length(arr) + sum(abs.(len))`.

# Examples

```julia-repl
# Create an array that will be padded
julia> my_array = rand(5)
5-element Vector{Float64}:
 0.0420017254437951
 0.19179144973603235
 0.5388760239550549
 0.6973699906283798
 0.9966598131018376

 # Pad the array with zeros before the original array
julia> pad_array(my_array, -2, 0)
7-element Vector{Float64}:
 0.0
 0.0
 0.0420017254437951
 0.19179144973603235
 0.5388760239550549
 0.6973699906283798
 0.9966598131018376

# Pad the array with the value 5 before and after the original array
julia> pad_array(my_array, (-2, 1), 5)
8-element Vector{Float64}:
 5.0
 5.0
 0.0420017254437951
 0.19179144973603235
 0.5388760239550549
 0.6973699906283798
 0.9966598131018376
 5.0
```
