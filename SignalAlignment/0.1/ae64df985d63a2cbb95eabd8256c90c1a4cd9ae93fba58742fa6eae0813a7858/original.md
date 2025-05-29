```
align_signals(signals, method; master = Index(1), by = nothing, output = Indices())
```

Align all signals in the vector `signals`.

# Arguments:

  * `signals`: A vector of signals
  * `method`: Any of `Delay, XcorrDelay, DTWDelay, Warp`
  * `master`: The signal to align all others to, e.g., `Index(1), Longest(), Shortest(), Centroid(), Barycenter()`
  * `by`: An optional function applied to the signals before aligning
  * `output`: `Indices()` or `Signals()`. The default is to output the indices that align the signals. If `output = Signals()`, the aligninment is applied and the aligned signals are returned.
