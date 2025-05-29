```julia
param_bootstrap_result(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    auxmomsim::MomentMatching.AuxiliaryParameters,
    Nseeds::Integer,
    Nsamplesim::Integer,
    Ndata::Integer;
    cs,
    saving,
    filename_suffix,
    errorcatching
) -> Any

```

Performs bootstrap and computes related quantities.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * mmsolu: Instance of EstimationResult. See separate documentation [`EstimationResult`](@ref).
  * auxmomsim: Contains the numerical parameters used to simulate the distribution of moments when model and the estimated parameters are assumed to be correct. Its format is not restricted, but `defaultInnerAuxStructure(mode,auxmomsim)` should return a valid aux structure. Should imitate the process generating the data, based on which the original moments were computed.
  * nprepeat: Contains the numerical parameters used in simulation when reestimating the parameters of the model with alternative moments to match and different seeds. Its format is not restricted, but `defaultInnerAuxStructure(mode,auxmomsim)` should return a valid aux structure. Should imitate the setup of the original estimation.
  * Nseeds: Number of different seeds to try for each alternative sample moment vector.
  * Nsamplesim: Number of alternative sample moment vectors to try.
  * Ndata: Size of data sample.

# Optional arguments

  * saving: Logical, true if results are to be saved.
  * filename_suffix: String with suffix to be used for file name when saving.
