```
davidchacklai(ds::DeterministicIteratedMap, n::Int, ics, m::Int; kwargs...) -> fps
```

Find periodic orbits `fps` of orders `1` to `n` for the map `ds` using the algorithm propesed by Davidchack & Lai[Davidchack1999](@cite). `ics` is a collection of initial conditions (container of vectors) to be evolved. `ics` will be used to detect periodic orbits of orders `1` to `m`. These `m`  periodic orbits will be used to detect periodic orbits of order `m+1` to `n`. `fps` is a vector with `n` elements. `i`-th element is a periodic orbit of order `i`.

## Keyword arguments

  * `β = nothing`: If it is nothing, then `β(n) = 10*1.2^n`. Otherwise can be a   function that takes period `n` and return a number. It is a parameter mentioned  in the paper[Davidchack1999](@cite).
  * `maxiters = nothing`: If it is nothing, then initial condition will be iterated `max(100, 4*β(p))` times (where `p` is the order of the periodic orbit)  before claiming it has not converged. If an integer, then it is the maximum   amount of iterations an initial condition will be iterated before claiming   it has not converged.
  * `disttol = 1e-10`: Distance tolerance. If `norm(f^{n}(x)-x) < disttol`   where `f^{n}` is the `n`-th iterate of the dynamic rule `f`, then `x`   is an `n`-periodic point.
  * `abstol = 1e-8`: A detected periodic point isn't stored if it is in `abstol`   neighborhood of some previously detected point. Distance is measured by   euclidian norm. If you are getting duplicate periodic points, increase this value.

## Description

The algorithm is an extension of Schmelcher & Diakonos[Schmelcher1997](@cite) implemented in [`periodicorbits`](@ref).

The algorithm can detect periodic orbits by turning fixed points of the original map `ds` to stable ones, through the transformation

$$
\mathbf{x}_{n+1} = \mathbf{x}_{n} + 
[\beta |g(\mathbf{x}_{n})| C^{T} - J(\mathbf{x}_{n})]^{-1} g(\mathbf{x}_{n})
$$

where

$$
g(\mathbf{x}_{n}) = f^{n}(\mathbf{x}_{n}) - \mathbf{x}_{n}
$$

and

$$
J(\mathbf{x}_{n}) = \frac{\partial g(\mathbf{x}_{n})}{\partial \mathbf{x}_{n}}
$$

The main difference between Schmelcher & Diakonos[Schmelcher1997](@cite) and  Davidchack & Lai[Davidchack1999](@cite) is that the latter uses periodic points of previous period as seeds to detect periodic points of the next period. Additionally, [`periodicorbits`](@ref) only detects periodic points of a given order,  while `davidchacklai` detects periodic points of all orders up to `n`.

## Important note

For low periods `n` circa less than 6, you should select `m = n` otherwise the algorithm  won't detect periodic orbits correctly. For higher periods, you can select `m` as 6.  We recommend experimenting with `m` as it may depend on the specific problem.  Increase `m` in case the orbits are not being detected correctly.

Initial conditions `ics` can be selected as a uniform grid of points in the state space or  subset of a chaotic trajectory.
