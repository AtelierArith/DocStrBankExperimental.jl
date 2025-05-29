structuretensor - Compute structure tensor values over an image

```
Usage:  (Ix2, Iy2, Ixy) = structuretensor(img, sigma=1)

Arguments: 
           img   - Image to be processed  ::Array{T,2}
           sigma - Standard deviation of Gaussian summation window. Typical
                   values to use might be 1-3. Default is 1.
Returns:
           Ix2   - 2nd moment of gradients in x
           Iy2   - 2nd moment of gradients in y
           Ixy   - 2nd moment of gradients in xy
```

See also: shi_tomasi(), harris(), noble(), coherence(), derivative5()
