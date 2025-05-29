```julia
two_stage_estimation(
    estset::MomentMatching.EstimationSetup,
    auxmomsim::MomentMatching.AuxiliaryParameters,
    Nseeds::Integer,
    Nsamplesim::Integer,
    Ndata::Integer;
    aux,
    npmm,
    saving,
    saving_bestmodel,
    filename_suffix,
    errorcatching
)

```

Two-step estimation procedure.

# Required arguments

  * estset: Instance of EstimationSetup. See separate documentation [`EstimationSetup`](@ref).
  * npmomsim: Contains the numerical parameters used to simulate the distribution of moments when model and the estimated parameters are assumed to be correct. Its format is not restricted, but `defaultInnerAuxStructure(mode,npmomsim)` should return a valid aux structure. Should imitate the process generating the data, based on which the original moments were computed.
  * nprepeat: Contains the numerical parameters used in simulation when reestimating the parameters of the model with alternative moments to match and different seeds. Its format is not restricted, but `defaultInnerAuxStructure(mode,npmomsim)` should return a valid aux structure. Should imitate the setup of the original estimation.
  * Nseeds: Number of different seeds to try for each alternative sample moment vector.
  * Nsamplesim: Number of alternative sample moment vectors to try.
  * Ndata: Size of data sample.

# Optional arguments

  * npmm: Numerical parameters for estimation. See separate documentation [`NumParMM`](@ref).
  * saving_est: Logical, true if estimation results are to be saved.
  * saving_bestmodel: Logical, if some object linked to model solution corresponding to the best parameters are to be saved.
  * filename_suffix: String with suffix to be used for file name when saving.
