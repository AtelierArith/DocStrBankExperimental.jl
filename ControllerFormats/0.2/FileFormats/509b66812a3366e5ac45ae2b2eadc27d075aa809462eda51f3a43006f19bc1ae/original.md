```
write_NNet(N::FeedforwardNetwork, filename::String)
```

Write a neural network to a file in [`NNet`](https://github.com/sisl/NNet) format.

### Input

  * `N`        – feedforward neural network
  * `filename` – name of the output file

### Output

`nothing`. The network is written to the output file.

### Notes

The NNet format assumes that all layers but the output layer use ReLU activation (the output layer uses the identity activation).

Some non-important part of the output (such as the input domain) is not correctly written and instead set to `0`.

See [`read_NNet`](@ref) for the documentation of the format.
