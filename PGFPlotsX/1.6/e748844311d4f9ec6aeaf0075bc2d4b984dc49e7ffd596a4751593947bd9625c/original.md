```
Table([options], ...; ...)
```

Tabular data with options, corresponding to `table[options] { ... }` in PGFPlots.

`options` stores the options. If that is followed by an `AbstractString`, that will be used as a filename to read data from, otherwise all the arguments are passed on to [`TableData`](@ref).

Examples:

```julia
Table(["x" => 1:10, "y" => 11:20])        # from a vector

Table([1:10, 11:20])                      # same contents, unnamed

Table(Dict(:x => 1:10, :y = 11:20))       # a Dict with symbols

@pgf Table({ "x index" = 2, "y index" = 1 }, randn(10, 3))

let x = range(0; stop = 1, length = 10), y = range(-2; stop =  3, length = 15)
    Table(x, y, sin.(x + y'))             # edges & matrix
end
```
