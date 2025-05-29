```
LocalKriging(method, localaniso, γ, μ=nothing, localanisohd=nothing)
```

LocalKriging estimation solver where `method` can be :MovingWindows or :KernelConvolution; `γ` is the variogram model and `μ` is the mean in case simple kriging is used. `localanisohd`is only necessary for :KernelConvolution and it is automatically passed via NN from `localaniso` if not informed.
