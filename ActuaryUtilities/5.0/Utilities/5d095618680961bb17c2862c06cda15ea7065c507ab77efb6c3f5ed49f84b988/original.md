```
accum_offset(x; op=*, init=1.0)
```

A shortcut for the common operation wherein a vector is scanned with an operation, but has an initial value and the resulting array is offset from the traditional accumulate. 

This is a common pattern when calculating things like survivorship given a mortality vector and you want the first value of the resulting vector to be `1.0`, and the second value to be `1.0 * x[1]`, etc.

Two keyword arguments:

  * `op` is the binary (two argument) operator you want to use, such as `*` or `+`
  * `init` is the initial value in the returned array

# Examples

```julia=repl
julia> accum_offset([0.9, 0.8, 0.7])
3-element Array{Float64,1}:
 1.0
 0.9
 0.7200000000000001

julia> accum_offset(1:5) # the product of elements 1:n, with the default `1` as the first value
5-element Array{Int64,1}:
  1
  1
  2
  6
 24

julia> accum_offset(1:5,op=+)
5-element Array{Int64,1}:
  1
  2
  4
  7
 11

```
