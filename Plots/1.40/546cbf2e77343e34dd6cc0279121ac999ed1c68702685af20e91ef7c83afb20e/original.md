```
bar(x,y)
bar!(x,y)
```

Make a bar plot of `y` vs `x`.

# Keyword arguments

  * `bar_position::Symbol`: Choose from `:overlay` (default),                  `:stack`. (warning: may only be partially                  implemented). Aliases: (:bar_positions, :barpositions).
  * `bar_width::Real`:  Width of bars in data coordinates. When               `nothing`, chooses based on `x` (or `y` when               `orientation = :h`). Aliases: (:bar_widths, :barwidths).
  * `bar_edges::Bool`: Align bars to edges (true), or centers               (the default) ?.
  * `fillrange::Union{Real, AbstractVector}`: Fills area between               fillrange and `y` for line-types, sets the base for               `bar`, `sticks` types, and similar for other types.               Aliases: (:fill_between, :fillbetween, :fillranges,               :fillrng, :fillto, :frange).
  * `permute::Tuple{Symbol, Symbol}`: Permutes data and axis             properties of the axes given in the tuple, e.g. (:x, :y).             Aliases: (:permutes,).

# Examples

```julia-repl
julia> bar([1,2,3],[4,5,6],fillcolor=[:red,:green,:blue],fillalpha=[0.2,0.4,0.6])
julia> bar([(1,4),(2,5),(3,6)])
```
