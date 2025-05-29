```
`determine_E(inputs...)`
```

Determine all E-series that contain each of the given inputs. The inputs are comma-seperated. The outputs are a vector of the names of possible series as `Symbol`s.

# Examples

```julia-repl
julia> determine_E(220, 470, 680)
3-element Vector{Symbol}:
 :E6
 :E12
 :E24

julia> determine_E(220, 470, 910)
1-element Vector{Symbol}:
 :E24
```
