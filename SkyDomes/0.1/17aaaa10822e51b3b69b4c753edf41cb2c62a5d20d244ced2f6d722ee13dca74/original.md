```
CIE(;type = 1, θₛ = 0.0, Φₛ = 0.0, rtol = sqrt(eps(Float64)), atol = 0.0,
```

maxevals = typemax(Int))

Create a standard CIE model of sky diffuse radiance on the horizontal plane as described by Darula and Kittler (2002). The argument `type` can have values from 1 to 15 representing the 15 standard CIE models. θₛ and Φₛ are the zenith and azimuth angles of the solar disc. `rtol` and `atol` and `maxevals` are the relative tolerance, absolute tolerance and maximum number of function evaluation of the numerical integration algorithm. See package documentation for details.
