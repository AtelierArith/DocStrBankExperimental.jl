```
matrixelement(ion, transition::Tuple, laser, chamber::Chamber, time::Real)
```

Calls `matrixelement(ion, transition, I, ϵhat, khat, Bhat)` with `I`, `ϵhat`, and `khat` evaluated for `laser` at time `time`, and `Bhat` evaluated for `chamber`.

`ion` may be either an Ion or an Int indicating the desired ion's index within `chamber`. `laser` may be either a Laser or an Int indicating the desired laser's index within `chamber`. `ion` and `laser` must either both be indices or both their respective Structs.
