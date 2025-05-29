```
@format [style::Symbol] [decorations::Bool] [sigfigs::Integer]
```

The `@format` macro provides a simple interface to control the output format for intervals. These options are passed to the `setformat` function. It returns the new `DisplayParameters` object.

The arguments may be in any order and of type:

  * `Symbol`: the output format (`:full`, `:standard` or `:midpoint`)
  * `Bool`: whether to display decorations
  * `Integer`: the number of significant figures

E.g.

```
julia> x = 0.1..0.3
@[0.0999999, 0.300001]

julia> @format full
Display parameters:
- format: full
- decorations: false
- significant figures: 6

julia> x
Interval(0.09999999999999999, 0.30000000000000004)

julia> @format standard 3
Display parameters:
- format: standard
- decorations: false
- significant figures: 3

julia> x
[0.0999, 0.301]
```
