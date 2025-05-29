`AbstractEpiModel`

Abstract supertype for all epidemiological models. To be used in `run_complex_contagion`, subtypes must implement

  * `model_states(::model)` which returns a tuple of symbols that describe the model states
  * `spreading_states(::model)` returning a dict of transitions describing the infector state, the state of soon to be infected (from and to) and the rate, e.g. `Dict(:I=>[(:S,:I, x.beta)])`
  * `trans_independent(::model)` which is a list of all the independent transitions with their rate (e.g., `[(:I,:R, x.gamma)]` for the SIR model
  * `first_active_states(::model)` which describes the seed states (e.g. `(:I,)` for the SIR)
