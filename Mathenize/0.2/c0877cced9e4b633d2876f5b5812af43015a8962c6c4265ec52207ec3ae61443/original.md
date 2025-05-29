```
calculate(math::String, print_info::Bool=false)
```

Return calculated value(s) in a string. 

# Arguments

  * `math::String` Math operation.
  * `print_info::Bool` Shows log of what happened during the calculation.

# Examples

```julia-repl
julia> calculate("sqrt(complex(-90)) + 10im")
0.0 + 19.486832980505138im
```
