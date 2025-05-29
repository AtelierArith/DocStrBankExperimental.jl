adapt_rb!(s, r, α)

Rao-Blackwellised adaptation step of Adaptive Metropolis as suggested by Andrieu & Thoms (Statist. Comput. 2008).

# Arguments:

  * `s`: AdaptiveMetropolis object
  * `r`: RWMState object
  * `α`: Acceptance rate

NB: This function should be called *before* calling accept!(r).
