```
read_Sherlock(filename::String)
```

Read a neural network stored in [Sherlock](https://github.com/souradeep-111/sherlock/blob/bf34fb4713e5140b893c98382055fb963230d69d/sherlock-network-format.pdf) format.

### Input

  * `filename` – name of the Sherlock file

### Output

A [`FeedforwardNetwork`](@ref).

### Notes

All layers including the output layer implicitly use a ReLU activation function.
