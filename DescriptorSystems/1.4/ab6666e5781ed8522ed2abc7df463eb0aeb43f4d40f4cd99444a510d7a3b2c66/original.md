```
Rval = evalfr(R; fval = 0)
```

Evaluate the rational transfer function matrix `R(λ)` for `λ = val`, where `val = im*fval`  for a continuous-time system or `val = exp(im*fval*abs(Ts))` for a discrete-time system,  with `Ts` the system sampling time.  
