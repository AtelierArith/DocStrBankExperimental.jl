```
Chunk(;
    N = 1,
    L = 1.0,
    time_created = 0.0,
    k = 1, 
    act = 0.0, 
    recent = [0.0],
    reps = 0, 
    lags = Float64[], 
    bl = zero(typeof(act)),
    slots...)
```

An object representing a declarative memory chunk.

# Keywords

  * `N=1.0`: number of uses
  * `L=1.0`: lifetime of chunk
  * `time_created=0.0`: time at which the chunk was created
  * `k=1`: number of chunks in recent set (k=1 is sufficient)
  * `act=0.0`: total activation
  * `act_blc=0.0`: base level constant component of activation
  * `act_bll=0.0`: base level learning component of activation
  * `act_pm=0.0`: partial matching component of activation
  * `act_sa=0.0`: spreading activation component of activation
  * `act_noise=0.0`: noise component of activation
  * `slots`: chunk slot-value pairs
  * `reps=0`: number of identical chunks. This can be used in simple cases to speed up the code.
  * `recent=[0.0]`: time stamps for k recent retrievals
  * `lags=Float64[]`: lags for recent retrievals (L - recent)
  * `bl=0.0`: baselevel constant added to chunks activation

# Example

```@example
using ACTRModels

chunk = Chunk(; name = :Bonkers, animal = :rat)
```
