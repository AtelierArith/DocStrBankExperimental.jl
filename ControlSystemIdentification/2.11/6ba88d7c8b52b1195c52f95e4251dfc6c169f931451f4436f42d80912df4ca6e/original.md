```
coherenceplot(d, [(;n=..., noverlap=...); hz=false)
```

Calculates and plots the (squared) coherence Function κ. κ close to 1 indicates a good explainability of energy in the output signal by energy in the input signal. κ << 1 indicates that either the system is nonlinear, or a strong noise contributes to the output energy.

`hz` indicates Hertz instead of rad/s

Keyword arguments to `coherence` are supplied as a named tuple as a second positional argument .
