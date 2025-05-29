```
EnsembleModel(model,
              atomic_weights=Float64[],
              bagging_fraction=0.8,
              n=100,
              rng=GLOBAL_RNG,
              acceleration=CPU1(),
              out_of_bag_measure=[])
```

Create a model for training an ensemble of `n` clones of `model`, with optional bagging. Ensembling is useful if `fit!(machine(atom, data...))` does not create identical models on repeated calls (ie, is a stochastic model, such as a decision tree with randomized node selection criteria), or if `bagging_fraction` is set to a value less than 1.0, or both.

Here the atomic `model` must support targets with scitype `AbstractVector{<:Finite}` (single-target classifiers) or `AbstractVector{<:Continuous}` (single-target regressors).

If `rng` is an integer, then `MersenneTwister(rng)` is the random number generator used for bagging. Otherwise some `AbstractRNG` object is expected.

The atomic predictions are optionally weighted according to the vector `atomic_weights` (to allow for external optimization) except in the case that `model` is a `Deterministic` classifier, in which case `atomic_weights` are ignored.

The ensemble model is `Deterministic` or `Probabilistic`, according to the corresponding supertype of `atom`. In the case of deterministic classifiers (`target_scitype(atom) <: Abstract{<:Finite}`), the predictions are majority votes, and for regressors (`target_scitype(atom)<: AbstractVector{<:Continuous}`) they are ordinary averages.  Probabilistic predictions are obtained by averaging the atomic probability distribution/mass functions; in particular, for regressors, the ensemble prediction on each input pattern has the type `MixtureModel{VF,VS,D}` from the Distributions.jl package, where `D` is the type of predicted distribution for `atom`.

Specify `acceleration=CPUProcesses()` for distributed computing, or `CPUThreads()` for multithreading.

If a single measure or non-empty vector of measures is specified by `out_of_bag_measure`, then out-of-bag estimates of performance are written to the training report (call `report` on the trained machine wrapping the ensemble model).

*Important:* If per-observation or class weights `w` (not to be confused with atomic weights) are specified when constructing a machine for the ensemble model, as in `mach = machine(ensemble_model, X, y, w)`, then `w` is used by any measures specified in `out_of_bag_measure` that support them.
