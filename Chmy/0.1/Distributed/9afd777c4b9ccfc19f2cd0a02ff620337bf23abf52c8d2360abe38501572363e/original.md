```
exchange_halo!(side::Side, dim::Dim, arch, grid, fields...)
```

Perform halo exchange communication between neighboring processes in a distributed architecture.

# Arguments

  * `side`: The side of the grid where the halo exchange is performed.
  * `dim`: The dimension along which the halo exchange is performed.
  * `arch`: The distributed architecture used for communication.
  * `grid`: The structured grid on which the halo exchange is performed.
  * `fields...`: The fields to be exchanged.
