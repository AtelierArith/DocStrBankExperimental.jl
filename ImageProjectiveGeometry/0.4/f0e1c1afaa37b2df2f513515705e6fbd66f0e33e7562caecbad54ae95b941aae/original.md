gaussfilt -  Small wrapper function for convenient Gaussian filtering

```
Usage:  smimg = gaussfilt(img, sigma)

Arguments:  img - Image to be smoothed, can be multi-channel.
                  ::Array{T,2}  or ::Array{T,3}
          sigma - Standard deviation of Gaussian filter.

Returns:  smimg - Smoothed image.
```

If called with sigma = 0 the function immediately returns with img assigned to smimg
