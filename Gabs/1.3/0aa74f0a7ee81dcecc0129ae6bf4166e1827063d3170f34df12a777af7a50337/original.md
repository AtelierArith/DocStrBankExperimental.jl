```
fidelity(state1::GaussianState, state2::GaussianState; tol::Real = 128 * eps(1))
```

Calculate the joint fidelity of two Gaussian states, defined as

$$
F(\rho, \sigma) = Tr(\sqrt{\sqrt{\rho} \sigma \sqrt{\rho}}).
$$

See: Banchi, Braunstein, and Pirandola, Phys. Rev. Lett. 115, 260501 (2015)

# Arguments

  * `state1`, `state2`: Gaussian states whose joint fidelity is to be calculated.
  * `tol`: Tolerance (inclusive) above the cut-off at $1$ for computing $x + \sqrt{x^2 - 1}$.
