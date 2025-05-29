```julia
set!(S::SpeedyWeather.AbstractSimulation; kwargs...) -> Any

```

Sets properties of the simuluation `S`. Convenience wrapper to call the other concrete  `set!` methods. All `kwargs` are forwarded to these methods, which are documented  seperately. See their documentation for possible `kwargs`. 
