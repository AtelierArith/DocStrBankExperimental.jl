```
integral(h; width=false)
```

Get the integral a histogram; `width` means multiply each bincount by their bin width when calculating the integral.

!!! warning
    `width` keyword argument only works with 1D histogram at the moment.


!!! warning
    Be aware of the approximation you make when using `width=true` with histogram with overflow bins, the overflow bins (i.e. the left/right most bins) width will be taken "as is".

