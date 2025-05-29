```
KernelSmoothing(X::SmoothedFreqTab; kernel = :Gaussian, hX = 0.622, scale = X.table.scale)
```

Returns Kernel smoothed frequency table as `KernelFreqTab`.

# Arguments

  * `X` the object which class is `freqtab`

## Optional Arguments

  * `kernel`
  * `hX` The band width.
  * `newint` A new interval to depict the continuized probability line.

# Value

`KernelFreqTab`

In the kernel smoothing, the choice of bandwidth `hX` is an important consideration. When bandwidth is large, the smoothed distribution becomes linear equating fucnction. Contrary, bandwidth is small, it becomes spikye shaped distribution. We recommend to use default value `hX = 6.22` or select it by using `EstBandwidth`.
