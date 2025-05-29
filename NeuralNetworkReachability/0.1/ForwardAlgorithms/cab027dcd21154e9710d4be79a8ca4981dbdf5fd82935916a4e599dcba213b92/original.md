```
Verisig{R} <: ForwardAlgorithm
```

Forward algorithm for sigmoid and tanh activation functions from [IvanovWAPL19](@citet).

### Fields

  * `algo` – reachability algorithm of type `TMJets`

### Notes

The implementation is known to be unsound in some cases.

The implementation currently only supports neural networks with a single hidden layer.
