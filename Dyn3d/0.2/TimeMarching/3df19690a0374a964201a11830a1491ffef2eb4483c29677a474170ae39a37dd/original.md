```
(scheme::HERKBody)(sᵢₙ, bd)
```

The object-like function of type HERKBody gets updated during timemarching.

# Arguments

  * `sᵢₙ` : solution of the last step, containing current time, timestep, qJ, v         and λ
  * `bd` : BodyDyn object, containing all bs, js and sys info that needs to be updated
