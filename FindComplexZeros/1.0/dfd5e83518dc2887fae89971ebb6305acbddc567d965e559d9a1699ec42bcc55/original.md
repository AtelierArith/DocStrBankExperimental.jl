```
findZerosWithSubdivision(upper_left, lower_right, f::Function, err=0.01, increment = err/100, dif=0.5)
```

Find locations of zeros of a function within a given rectangular domain

Each line of result contains the upper left, lower right corner of the rectangular box that contains the zero

# Arguments

  * `upper_left`: a complex number that is the upper left corner of rectangular domain
  * `lower_right`: a complex number that is the lower right corner of rectangular domain
  * `f::Function`: the function
  * `err=0.001`: error of the location of each zero
  * `increment=err/100`: step size of the `countZeros` function
  * `dif=0.5`: when the difference between $arg(f(z))$ at 2 consecutive points of

evaluation by the `countZeros` function is greater than `2pi-dif`, a jump point is registered

# Example

```julia-repl
julia> function exp_sum(x)
    return (1+im)*exp(x) + (3.5+2*im) + (3-im)*exp(-x)
end
exp_sum (generic function with 1 method)

julia> findZerosWithSubdivision(-10 + 10im, 10 - 10im, exp_sum, 0.01)
7-element Vector{Tuple{Any, Any}}:
 (0.859375 - 3.0859375im, 0.869140625 - 3.095703125im)
 (0.859375 - 9.375im, 0.869140625 - 9.384765]625im)
 (0.859375 + 9.47265625im, 0.869140625 + 9.462890625im)
 (0.859375 + 3.193359375im, 0.869140625 + 3.18359375im)
 (-0.068359375 + 1.9921875im, -0.05859375 + 1.982421875im)
 (-0.068359375 + 8.271484375im, -0.05859375 + 8.26171875im)
 (-0.068359375 - 4.287109375im, -0.05859375 - 4.296875im)
```
