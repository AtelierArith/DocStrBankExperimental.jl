```
set_schemes(;
    # keyword arguments and their default values
    time=SteadyState,
    divergence=Linear, 
    laplacian=Linear, 
    gradient=Orthogonal,
    limiter=nothing) = begin
    
    # Returns NamedTuple definition for scheme 
    (
        time=time,
        divergence=divergence,
        laplacian=laplacian,
        gradient=gradient,
        limiter=limiter
    )   
end
```

The `set_schemes` function is used at the top-level API to help users define discretisation schemes for every field solved. It offers default values, thus users can pick and choose which entry they wish to modify.

# inputs

  * `time` is used to set the time schemes (default is `SteadyState`)
  * `divergence` is used to set the divergence scheme (default is `Linear`)
  * `laplacian` is used to set the laplacian scheme (default is `Linear`)
  * `gradient`  is used to set the gradient scheme (default is `Orthogonal`)
  * `limiter` is used to specify if gradient limiters should be used, currently supported limiters include `FaceBased` and `MFaceBased` (default is `nothing`)
