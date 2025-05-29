```
J = imhdome(I::GMTimage{<:UInt8, 2}, H; conn=4)::GMTimage
```

### Args

  * `I::GMTimage{<:UInt8, 2}`: Input image.
  * `H`: height below the filling maskhdome; must be >= 0 (words of the Leptonica pixHDome() docs)

### Kwargs

  * `conn::Int=4`: Connectivity value used to identify the regional maxima in I (4 or 8). Default is 4.

### Returns

A new $GMTimage$ of the same type as `I`.
