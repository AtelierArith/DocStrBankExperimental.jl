```
sample(
    rng::AbstractRNG,
    h::Hamiltonian,
    κ::AbstractMCMCKernel,
    θ::AbstractVecOrMat{T},
    n_samples::Int,
    adaptor::AbstractAdaptor=NoAdaptation(),
    n_adapts::Int=min(div(n_samples, 10), 1_000);
    drop_warmup::Bool=false,
    verbose::Bool=true,
    progress::Bool=false
)
```

Sample `n_samples` samples using the proposal `κ` under Hamiltonian `h`.

  * The randomness is controlled by `rng`. 

      * If `rng` is not provided, `GLOBAL_RNG` will be used.
  * The initial point is given by `θ`.
  * The adaptor is set by `adaptor`, for which the default is no adaptation.

      * It will perform `n_adapts` steps of adaptation, for which the default is the minimum of `1_000` and 10% of `n_samples`
  * `drop_warmup` controls to drop the samples during adaptation phase or not
  * `verbose` controls the verbosity
  * `progress` controls whether to show the progress meter or not
