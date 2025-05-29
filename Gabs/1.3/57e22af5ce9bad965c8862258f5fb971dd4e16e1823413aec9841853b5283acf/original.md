```
entropy_vn(state::GaussianState; tol::Real = 128 * eps(1/2))
```

Calculate the Von Neumann entropy of a Gaussian state, defined as

$$
S(\rho) = -Tr(\rho \log(\rho)) = \sum_i f(v_i)
$$

such that $\log$ denotes the natural logarithm, $v_i$ is the symplectic spectrum of $\mathbf{V}/\hbar$, and the $f$ is taken to be

$$
f(x) = (x + 1/2) \log(x + 1/2) - (x - 1/2) \log(x - 1/2)
$$

wherein it is understood that $0 \log(0) \equiv 0$.

# Arguments

  * `state`: Gaussian state whose Von Neumann entropy is to be calculated.
  * `tol`: Tolerance (exclusive) above the cut-off at $1/2$ for computing $f(x)$.
