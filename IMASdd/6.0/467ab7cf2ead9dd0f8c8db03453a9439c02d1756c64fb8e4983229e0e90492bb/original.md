```
selective_copy!(@nospecialize(h_in::IDS), @nospecialize(h_out::IDS), path::Vector{<:AbstractString}, time0::Float64)
```

Copies the content of a path from one IDS to another (if the path exists) at a given time0

NOTE:

  * the path is a i2p(ulocation)
  * if time0 is NaN then all times are retained
