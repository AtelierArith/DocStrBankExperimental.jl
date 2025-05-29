```
uniform(xs;channels=false)
```

Promote the sample rate (and optionally the number of channels) to be the highest sample rate (and optionally channel count) of the passed value `xs`, an iterable of signals.

!!! note
    `uniform` rarely needs to be called directly. It is called implicitly, within the body of [`mapsignal`](@ref) for example.

