```
reflect(kernel) --> reflectedkernel
```

Compute the pointwise reflection around 0, 0, ... of the kernel `kernel`.  Using `imfilter` with a `reflectedkernel` performs convolution, rather than correlation, with respect to the original `kernel`.
