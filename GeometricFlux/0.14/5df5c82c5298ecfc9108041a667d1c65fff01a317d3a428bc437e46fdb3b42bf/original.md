```
VGAE(enc[, σ])
```

Variational graph autoencoder.

# Arguments

  * `enc`: encoder. It can be any graph convolutional layer.

Encoder is specified by user and decoder will be `InnerProductDecoder` layer.
