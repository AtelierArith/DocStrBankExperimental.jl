```
sigma(ion::Ion, ψ1::sublevel[, ψ2::sublevel])
```

Returns $|ψ1\rangle\langle ψ2|$, where $|ψ_i\rangle$ corresponds to the state returned by `ion[ψᵢ]`.

If ψ2 is not given, then $|ψ1\rangle\langle ψ1|$ is returned.
