```
standardMC(X::AbstractGraph, β::Real, iters::Integer; keywords...)
```

Runs `iters` iterations of a standard Metropolis Monte Carlo algorithm on the given Ising spin model `X`, at inverse temperature `β`. Each spin flip attempt counts as an iteration.

Returns two objects: a vector of energies and the last configuration (see [`Config`](@ref)).

Possible keyord arguments are:

  * `step`: the interval of iterations with which to collect energies (for the returned result) and to call the `hook` function (see below). The default is `1`, which is good for debugging but otherwise generally a bad idea.
  * `seed`: the random seed. The default is some arbitrary number.
  * `C0`: the initial configuration. The default is `nothing`, in which case it is initialized at random. Otherwise it can be a [`Config`](@ref) object. Passing the result of a previous run can be useful e.g. when implementing a simulated annealing protocol, or if the system has not equilibrated yet.
  * `hook`: a function to be executed after every `step` number of iterations (see above). It must take five arguments: the current iteration, the graph `X`, the current configuration, the number of accepted moves so far, and the current energy. Useful to collect data other than the energy, write to files ecc; you'd probably want to use a closure, see the example below. The return value must be a `Bool`: return `false` to interrupt the simulation, `true` otherwise. The default does nothing and just returns `true`.

Basic example:

```
julia> Random.seed!(76543); X = RRRMC.GraphPSpin3(3999, 5); β = 1.0;
julia> Es, C = standardMC(X, β, 100_000, step = 1_000);
```

Example of using the `hook` for collecting samples as the columns of a `BitMatrix`:

```
julia> iters = 100_000; step = 1_000; l = iters ÷ step; N = RRRMC.getN(X);
julia> Cs = BitArray(undef, N, l); hook = (it, X, C, acc, E) -> (Cs[:,it÷step]=C.s; true);
julia> Es, C = standardMC(X, β, iters, step = step, hook = hook);
```
