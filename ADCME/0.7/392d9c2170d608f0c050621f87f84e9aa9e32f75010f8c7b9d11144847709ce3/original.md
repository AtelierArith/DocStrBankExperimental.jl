```
αscheme_time(Δt::Array{Float64}; ρ::Float64 = 1.0)
```

Returns the integration time $t_{i+1-\alpha_{f_2}}$ between $[t_i, t_{i+1}]$ using the alpha scheme.  If $\Delta t$ has length $n$, the output will also have length $n$. 
