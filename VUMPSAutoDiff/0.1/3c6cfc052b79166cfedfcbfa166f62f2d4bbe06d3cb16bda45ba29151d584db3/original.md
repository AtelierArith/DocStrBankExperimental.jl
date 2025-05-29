```
overall_u1_phase(T1, T2)
```

Compute the global U(1) phase difference between two tensors. Returns a complex phase factor λ such that T1 ≈ λ*T2 up to numerical precision. Uses the trace of T1'*T2 to determine the phase.

# Arguments

  * `T1`, `T2`: Input tensors to compare

# Returns

  * Complex phase factor λ with |λ| = 1
