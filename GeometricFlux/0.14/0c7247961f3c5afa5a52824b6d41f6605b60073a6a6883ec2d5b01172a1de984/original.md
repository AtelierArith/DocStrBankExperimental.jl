```
GAE(enc, [σ=identity])
```

Graph autoencoder.

# Arguments

  * `enc`: encoder. It can be any graph convolutional layer.
  * `σ`: Activation function for decoder.

Encoder is specified by user and decoder will be `InnerProductDecoder` layer.
