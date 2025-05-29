```
struct YahooOpt <: AbstractQueryOpt
  period1  # the start time
  period2  # the end time
  interval # "1d", "1wk" or "1mo"
  events   # currently only `:history` supported
end
```

The Yahoo Finance HTTP API query object.

# Examples

```jl-repl
julia> t = Dates.now()
2020-08-09T01:38:04.735

julia> YahooOpt(period1 = t - Year(2), period2 = t)
YahooOpt{DateTime} with 4 entries:
  :period1  => 1533778685
  :period2  => 1596937085
  :interval => "1d"
  :events   => :history
```
