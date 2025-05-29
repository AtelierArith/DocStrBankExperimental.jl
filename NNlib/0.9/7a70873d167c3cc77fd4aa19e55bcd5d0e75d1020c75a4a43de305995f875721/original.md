```
DepthwiseConvDims
```

Concrete subclass of `ConvDims` for a depthwise convolution.  Differs primarily due to characterization by `C_in`, `C_mult`, rather than `C_in`, `C_out`.  Useful to be separate from DenseConvDims primarily for channel calculation differences.
