```
excite!(A, [nothing], spin, rf::InstantaneousRF, [nothing])
excite!(A, B, spin, rf::RF, [workspace])
```

Simulate excitation, overwriting `A` and `B` (in-place version of [`excite`](@ref)).
