```julia
struct ReversedFrame{df<:DataFrames.DataFrame}
```

  * `__df::DataFrames.DataFrame`
  * `__s::Dict`

This presents a reversed view of an entire DataFrame.

# Example

```julia-repl
julia> rf = ReversedFrame(btcusd) # btcusd is a DataFrame
julia> rf.ts[1] # the most recent timestamp
julia> rf.ts[2] # the timestamp before that
julia> rf.c[1]  # the close at 1 corresponds with the timestamp at 1
julia> rf.o[1] == btcusd.o[end]
true
```

  * Index 1 is the origin and represents the present time.
  * Higher indices go back in time.
  * This is similar to how series are indexed in TradingView's PineScript except they use a 0-based index.
