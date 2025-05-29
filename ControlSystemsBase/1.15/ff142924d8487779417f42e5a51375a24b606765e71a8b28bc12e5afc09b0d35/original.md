```
d2c_exact(sys::AbstractStateSpace{<:Discrete}, method = :causal)
```

Translate a discrete-time system to a continuous-time system by one of the substitutions

  * $z^{-1} = e^{-sT_s}$ if `method = :causal` (default)
  * $z = e^{sT_s}$  if `method = :acausal`

The translation is exact in the frequency domain, i.e., the frequency response of the resulting continuous-time system is identical to the frequency response of the discrete-time system.

This method of translation is useful when analyzing hybrid continuous/discrete systems in the frequency domain and high accuracy is required.

The resulting system will be be a static system in feedback with pure delays. When `method = :causal`, the delays will be positive, resulting in a causal system that can be simulated in the time domain. When `method = :acausal`, the delays will be negative, resulting in an acausal system that **can not** be simulated in the time domain. The acausal translation results in a smaller system with half as many delay elements in the feedback path.
