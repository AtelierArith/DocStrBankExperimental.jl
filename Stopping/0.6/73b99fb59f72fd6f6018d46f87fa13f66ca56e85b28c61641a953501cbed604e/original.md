Type: NLPStopping

Methods: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`,  `KKT`, `unconstrained_check`, `optim_check_bounded`

Specialization of `GenericStopping`. Stopping structure for non-linear optimization models using `NLPModels` ( https://github.com/JuliaSmoothOptimizers/NLPModels.jl ).

Attributes:

  * `pb`         : An `AbstractNLPModel`.
  * `current_state`      : The information relative to the problem, see `GenericState` or `NLPAtX`.
  * (opt) `meta` : Metadata relative to stopping criteria, see `StoppingMeta`.
  * (opt) `main_stp` : Stopping of the main loop in case we consider a Stopping                         of a subproblem.                         If not a subproblem, then `VoidStopping`.
  * (opt) `listofstates` : ListofStates designed to store the history of States.
  * (opt) `stopping_user_struct` : Contains any structure designed by the user.

Constructors: 

  * `NLPStopping(pb::AbstractNLPModel, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The default constructor.
  * `NLPStopping(pb::AbstractNLPModel, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The one passing the `kwargs` to the `stop_remote`.
  * `GenericStopping(pb::AbstractNLPModel, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The one passing the `kwargs` to the `meta`.
  * `GenericStopping(pb::AbstractNLPModel; n_listofstates=, kwargs...)`    The one setting up a default state `NLPAtX` using `pb.meta.x0`, and initializing the list of states if `n_listofstates>0`. The optimality function is the function `KKT` unless `optimality_check` is in the `kwargs`.

Notes:

  * Designed for `NLPAtX` State. Constructor checks that the State has the required entries.

```

```
