```
steady_force(q,panels,U=SVector(-1,0,0);kwargs...)
```

Integrated pressure force coefficient Cₚ =∫ₛ cₚ n da of `panels` with strengths `q`. where cₚ = 1-u²/U², `U` is the freestreeam velocity and u=U+∇Φ is the flow velocity. Computation is accelerated with multi-threading when `Threads.nthreads()>1`.
