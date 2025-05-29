```
polar_map(;z0 = -0.5)
```

Returns the polar map 
> `h:(θ,z)->((z-z0)cos(2πθ), (z-z0)sin(2πθ))`
as well as its derivative `HJ`, its inverse `hinv`, and its inverse derivative `HJinv`. Useful for applying extrapolation methods to maps on T×R. Default value of `z0` is useful for the standard map on T×[0,1] with k=0.7.
