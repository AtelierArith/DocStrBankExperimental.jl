```
gaussiansmooth3d(image)

gaussiansmooth3d(image, sigma=[5,5,5];
    mask=nothing,
    nbox=ifelse(isnothing(mask), 3, 6), 
    weight=nothing, dims=1:min(ndims(image),3), 
    boxsizes=getboxsizes.(sigma, nbox),
    padding=false
    )
```

Performs Gaussian smoothing on `image` with `sigma` as standard deviation of the Gaussian. By application of `nbox` times running average filters in each dimension. The length of `sigma` and the length of the `dims` that are smoothed have to match. (Default `3`)

Optional arguments:

  * `mask`: Smoothing can be performed using a mask to inter-/extrapolate missing values.
  * `nbox`: Number of box applications. Default is `3` for normal smoothing and `6` for masked smoothing.
  * `weight`: Apply weighted smoothing. Either weighted or masked smoothing can be porformed.
  * `dims`: Specify which dims should be smoothed. Corresponds to manually looping of the other dimensions.
  * `boxizes`: Manually specify the boxsizes, not using the provided sigma. `length(boxsizes)==length(dims) && length(boxsizes[1])==nbox`
  * `padding`: If `true`, the image is padded with zeros before smoothing and the padding is removed afterwards.
