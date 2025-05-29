```
pure_nash(nfg; ntofind=Inf, tol=1e-8)
```

Finds all pure action Nash equilibria for a normal form game. It returns an empty array if there is no pure action Nash.

Currently uses a brute force algorithm, but that hopefully will change in the future.

# Arguments

  * `nfg::NormalFormGame`: Instance of N-player NormalFormGame.
  * `ntofind::Inf`: Maximal number of pure action Nash equilibria to be found; default is `prod(nfg.nums_actions)`.
  * `tol::Real` : Tolerance to be used to determine best response actions.

# Returns

  * `ne::Vector{NTuple{N,Int}}`: Vector of pure action Nash equilibria.
