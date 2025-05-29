```
TurboDense{B=true}(activation, outputdim::Integer)
```

Linear (dense) layer.

  * `B` specifies whether the layer includes a bias term.
  * The `activation` function is applied elementwise to the result.
  * `outputdim` indicates how many dimensions the input is mapped to.

Randomly initializing weights using the (Xavier) Glorot normal distribution. The bias is zero-initialized.
