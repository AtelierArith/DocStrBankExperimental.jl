```julia
struct Lindblad <: OpenQuantumBase.AbstractInteraction
```

A Lindblad operator, define by a rate $γ$ and corresponding operator $L$`.

  * `γ`: Lindblad rate
  * `L`: Lindblad operator
  * `size`: size
