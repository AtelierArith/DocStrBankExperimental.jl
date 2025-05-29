Type: LAStopping

Methods: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`,  `linear_system_check`, `normal_equation_check`

Specialization of GenericStopping. Stopping structure for linear algebra solving either

$Ax = b$

or

$$
min\_{x} \tfrac{1}{2}\|Ax - b\|^2
$$

Attributes:

  * `pb`         : a problem using, for instance, either `LLSModel` (designed for linear least square problem, see https://github.com/JuliaSmoothOptimizers/LLSModels.jl ) or `LinearSystem`.
  * `current_state`      : The information relative to the problem, see `GenericState`.
  * (opt) `meta` : Metadata relative to stopping criteria, see `StoppingMeta`.
  * (opt) `main_stp` : Stopping of the main loop in case we consider a Stopping                         of a subproblem.                         If not a subproblem, then `VoidStopping`.
  * (opt) `listofstates` : ListofStates designed to store the history of States.
  * (opt) `stopping_user_struct` : Contains a structure designed by the user.

Constructors: 

  * `LAStopping(pb, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false)`    The default constructor.
  * `LAStopping(pb, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false, kwargs...)`    The one passing the `kwargs` to the `stop_remote`.
  * `LAStopping(pb, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), zero_start::Bool = false, kwargs...)`    The one passing the `kwargs` to the `meta`.
  * `LAStopping(:: Union{AbstractLinearOperator, AbstractMatrix}, :: AbstractVector; sparse::Bool = true, n_listofstates::Int = 0, kwargs...)`    The one setting up a default problem (`sparse ? LLSModel(A, b) : LinearSystem(A, b)`), a default `GenericState` using x, and initializing the list of states if `n_listofstates>0`.
  * `LAStopping(:: Union{AbstractLinearOperator, AbstractMatrix}, :: AbstractVector, :: AbstractState; sparse::Bool = true, kwargs...)`    The one setting up a default problem (`sparse ? LLSModel(A, b) : LinearSystem(A, b)`).

Notes:

  * No specific State targeted
  * State don't necessarily keep track of evals
  * Evals are checked only for `pb.A` being a LinearOperator
  * `zero_start` is true if 0 is the initial guess (not check automatically)
  * `LLSModel` counter follow `NLSCounters` (see `init_max_counters_NLS`)
  * By default, `meta.max_cntrs` is initialized with an NLSCounters

See also `GenericStopping`, `NLPStopping`, `linear_system_check`, `normal_equation_check`
