```
curves(x,y)
curves!(x,y)
```

Draw a Bezier curve from `(x[1],y[1])` to `(x[end],y[end])` with control points `(x[2],y[2]), ..., (x[end-1],y[end]-1)`.

# Keyword arguments

  * `fillrange::Union{Real, AbstractVector}`: Fills area between               fillrange and `y` for line-types, sets the base for               `bar`, `sticks` types, and similar for other types.               Aliases: (:fill_between, :fillbetween, :fillranges,               :fillrng, :fillto, :frange).

# Example

```julia-repl
julia> curves([1,2,3,4],[1,1,2,4])
```
