```
extremal_opt(X::AbstractGraph, τ::Real, iters::Integer; keywords...)
```

Extremal optimization algorithm: it seeks the lowest energy state of a given Ising spin model `X` by performing a random walk biased towards low-energy states, but with a heavy tail which allows it to avoid getting trapped.

The interface is very similar to that of [`standardMC`](@ref) and the other RRRMC Monte Carlo functions, but it takes a parameter `τ` instead of `β`, the return values are different, and the `hook` keyword argument has a different signature, see below.

The parameter `τ` controls the shape of the tail and should be larger than 1 (a reasonable value could be 1.3); `iters` is the total number of spin flips performed.

This function has a specialized version for [`DiscrGraph`](@ref) models; otherwise, it works but it is not implemented very efficiently at the moment (each spin flip takes O(N) time even on diluted graphs).

Returns 4 objects: the final configuration, the minimum energy found, the configuration of minimum energy, and the iteration at which such configuration was found (see [`Config`](@ref)).

Possible keyord arguments are:

  * `step`: the interval of iterations with which to call the `hook` function (see below). The default is `1`, which is good for debugging but otherwise generally a bad idea, probably.
  * `seed`: the random seed. The default is some arbitrary number.
  * `C0`: the initial configuration. The default is `nothing`, in which case it is initialized at random. Otherwise it can be a [`Config`](@ref) object.
  * `hook`: a function to be executed after every `step` number of iterations (see above). It must take five arguments: the current iteration, the graph `X`, the current configuration, the current energy, and the minimum energy found so far. Useful to collect data other than the energy, write to files ecc; you'd probably want to use a closure, see the example below. The return value must be a `Bool`: return `false` to interrupt the simulation, `true` otherwise. The default does nothing and just returns `true`. Note that the signature is similar to that of the corresponding `hook` argument in [`standardMC`](@ref), but different.

Basic example:

```
julia> Random.seed!(76543); X = RRRMC.GraphPSpin3(3999, 5); τ = 1.3;
julia> C, Emin, Cmin, itmin = extremal_opt(X, τ, 100_000, step = 1_000);
```

Example of using the `hook` for collecting samples as the columns of a `BitMatrix`:

```
julia> iters = 100_000; step = 1_000; l = iters ÷ step; N = RRRMC.getN(X);
julia> Cs = BitArray(undef, N, l); hook = (it, X, C, E, Emin) -> (Cs[:,it÷step]=C.s; true);
julia> C, Emin, Cmin, itmin = extremal_opt(X, τ, iters, step = step, hook = hook);
```
