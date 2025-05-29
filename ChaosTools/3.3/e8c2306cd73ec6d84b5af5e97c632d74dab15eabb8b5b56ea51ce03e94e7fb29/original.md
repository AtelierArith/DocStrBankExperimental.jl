```
gali(ds::DynamicalSystem, T, k::Int; kwargs...) -> GALI_k, t
```

Compute $\text{GALI}_k$[^Skokos2007] for a given `k` up to time `T`. Return $\text{GALI}_k(t)$ and time vector $t$.

The third argument sets the order of `gali`. `gali` function simply initializes a [`TangentDynamicalSystem`](@ref) with `k` deviation vectors and calls the method below. This means that the automatic Jacobian is used by default. Initialize manually a [`TangentDynamicalSystem`](@ref) if you have a hand-coded Jacobian.

## Keyword arguments

  * `threshold = 1e-12`: If `GALI_k` falls below the `threshold` iteration is terminated.
  * `Δt = 1`: Time-step between deviation vector normalizations. For continuous systems this is approximate.
  * `u0`: Initial state for the system. Defaults to `current_state(ds)`.

## Description

The Generalized Alignment Index, $\text{GALI}_k$, is an efficient (and very fast) indicator of chaotic or regular behavior type in $D$-dimensional Hamiltonian systems ($D$ is number of variables). The *asymptotic* behavior of $\text{GALI}_k(t)$ depends critically on the type of orbit resulting from the initial condition. If it is a chaotic orbit, then

$$
\text{GALI}_k(t) \sim
\exp\left[\sum_{j=1}^k (\lambda_1 - \lambda_j)t \right]
$$

with $\lambda_j$ being the `j`-th Lyapunov exponent (see [`lyapunov`](@ref), [`lyapunovspectrum`](@ref)). If on the other hand the orbit is regular, corresponding to movement in $d$-dimensional torus with $1 \le d \le D/2$ then it holds

$$
\text{GALI}_k(t) \sim
    \begin{cases}
      \text{const.}, & \text{if} \;\; 2 \le k \le d  \; \; \text{and}
      \; \;d > 1 \\
      t^{-(k - d)}, & \text{if} \;\;  d < k \le D - d \\
      t^{-(2k - D)}, & \text{if} \;\;  D - d < k \le D
    \end{cases}
$$

Traditionally, if $\text{GALI}_k(t)$ does not become less than the `threshold` until `T` the given orbit is said to be chaotic, otherwise it is regular.

Our implementation is not based on the original paper, but rather in the method described in[^Skokos2016b], which uses the product of the singular values of $A$, a matrix that has as *columns* the deviation vectors.

[^Skokos2007]: Skokos, C. H. *et al.*, Physica D **231**, pp 30–54 (2007)

[^Skokos2016b]: Skokos, C. H. *et al.*, *Chaos Detection and Predictability* - Chapter 5 (section 5.3.1 and ref. [85] therein), Lecture Notes in Physics **915**, Springer (2016)
