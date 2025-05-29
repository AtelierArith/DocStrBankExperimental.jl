```julia
fetchCliqHistoryAll!(smt)
fetchCliqHistoryAll!(smt, hist)

```

Fetch solver history from clique state machines that have completed their async Tasks and store in the `hist::Dict{Int,Tuple}` dictionary.
