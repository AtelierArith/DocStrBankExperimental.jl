```
optim_nnls(order)
```

Simple non-negative least squares method for regularization,  implemented using Optim.jl. All around effective, but can be slow for large problems, such as 2D inversions. It can be used as a "solver" for invert function.

`order` is an integer that determines the tikhonov matrix  (for more info look Hansen's 2010 book on inverse problems).  Order `n` means that the penalty term will be the n'th derivative of the results. 

`L` detemines which norm of the penalty term will be minimized.  Default is 2 (tikhonov regularization).
