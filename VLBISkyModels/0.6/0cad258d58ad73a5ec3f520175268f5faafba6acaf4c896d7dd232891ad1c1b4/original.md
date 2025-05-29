```julia
struct RaisedCosinePulse{T} <: VLBISkyModels.Pulse
```

```
RaisedCosinePulse()
RaisedCosinePulse(rolloff)
```

Raised cosine pulse function. This tends to be a very flat response, where the roll off controls the speed of decay. By default we set `rolloff = 0.5`.
