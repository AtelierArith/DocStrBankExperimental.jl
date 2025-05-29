```
browse(t; newwindow = false, kwargs...)
```

Browse data source in a new Blink window using Tables.jl's `showtable` function.

# Arguments

  * `t`, a Tables.jl-compatible data source, for example a `DataFrame` or a `NamedTuple` of `Vector`s
  * `newwindow`, boolean keyword argument to view the data in a new `Blink` window instead of over-writing. Viewing in a new window will be slower than over-writing.
  * `kwargs...`, keyword arguments passed to the `showtable` command from TableView.jl to control the details of the new data viewer. See [`showtable`](@ref) for details.

# Examples

```julia
julia> t = (a = rand(10), b = rand(10))

julia> browse(t)
```

```julia
julia> t = rand(100, 100)

julia> browse(t, dark = true)
```

See also: [`showtable`](@ref)
