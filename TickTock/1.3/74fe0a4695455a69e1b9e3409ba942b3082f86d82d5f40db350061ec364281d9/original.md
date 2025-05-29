```
peektimers()
```

Return the elapsed seconds counted by all timers, without stopping them, as an array.

## Example

```
julia> laptimer()
3         [ Info:         16.380142899s: 16 seconds, 380 milliseconds
2         [ Info:         21.480662472s: 21 seconds, 480 milliseconds
1         [ Info:         23.888862411s: 23 seconds, 888 milliseconds

julia> peektimers()
3-element Vector{Float64}:
 18.56985403
 23.670373603
 26.078573542
```
