```
add_sdp_variables(m, net::Network{MultiPhase})
```

Create complex variables:

  * `m[:w]` are 3x3 Hermitian matrices of voltage squared (V*V^T)
  * `m[:l]` are 3x3 Hermitian matrices of current squared (I*I^T)
  * `m[:sj]` are 3x1 matrices of net power injections (at bus j)
  * `m[:Sij]` are 3x3 Complex matrices of line flow powers (from i to j)

Also:

  * `m[:H]` are 3x3 Hermitian matrices of the positive semi-definite constraints
