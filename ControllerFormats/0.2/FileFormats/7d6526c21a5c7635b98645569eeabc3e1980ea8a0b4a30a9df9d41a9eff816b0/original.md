```
write_Sherlock(N::FeedforwardNetwork, filename::String)
```

Write a neural network to a file in [Sherlock](https://github.com/souradeep-111/sherlock/blob/bf34fb4713e5140b893c98382055fb963230d69d/sherlock-network-format.pdf) format.

### Input

  * `N`        – feedforward neural network
  * `filename` – name of the output file

### Output

`nothing`. The network is written to the output file.

### Notes

The Sherlock format requires that all activation functions are ReLU.
