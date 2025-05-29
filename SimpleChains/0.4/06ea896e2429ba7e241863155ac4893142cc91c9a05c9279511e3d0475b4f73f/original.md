```
Conv(activation, dims::Tuple{Vararg{Integer}}, outputdim::Integer)
```

Performs a convolution with `dims` and maps it to `outputdim` output channels, then adds a bias (one per `outputdim`) and applies `activation` elementwise.

E.g., `Conv(relu, (5, 5), 16)` performs a `5 × 5` convolution, and maps the input channels to 16 output channels, before adding a bias and applying `relu`.

Randomly initializing weights using the (Xavier) Glorot uniform distribution. The bias is zero-initialized.
