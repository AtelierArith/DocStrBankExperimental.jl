```
DeltaMeta(method = ..., [ inverse = ... ])
```

`DeltaMeta` structure specifies the approximation method for the outbound messages in the `DeltaFn` node. 

# Arguments

  * `method`: required, the approximation method, currently supported methods are [`Linearization`](@ref), [`Unscented`](@ref) and [`CVI`](@ref).
  * `inverse`: optional, if no inverse provided, the backward rule will be computed based on RTS (Petersen et al. 2018; On Approximate Delta Gaussian Message Passing on Factor Graphs)

Is is also possible to pass the `AbstractApproximationMethod` to the meta of the delta node directly. In this case `inverse` is set to `nothing`.
