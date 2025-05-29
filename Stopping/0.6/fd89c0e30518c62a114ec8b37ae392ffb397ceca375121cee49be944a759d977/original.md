Type: `GenericStopping`

Methods: `start!`, `stop!`, `update_and_start!`, `update_and_stop!`, `fill_in!`, `reinit!`, `status`

A generic Stopping to solve instances with respect to some  optimality conditions. Optimality is decided by computing a score, which is then  tested to zero.

Tracked data include:

  * `pb`         : A problem
  * `current_state` : The information relative to the problem, see `GenericState`.
  * (opt) `meta` : Metadata relative to a stopping criteria, see `StoppingMeta`.
  * (opt) `main_stp` : Stopping of the main loop in case we consider a Stopping                      of a subproblem.                      If not a subproblem, then `VoidStopping`.
  * (opt) `listofstates` : `ListofStates` designed to store the history of States.
  * (opt) `stopping_user_struct` : Contains a structure designed by the user.

Constructors: 

  * `GenericStopping(pb, meta::AbstractStoppingMeta, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The default constructor.
  * `GenericStopping(pb, meta::AbstractStoppingMeta, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The one passing the `kwargs` to the `stop_remote`.
  * `GenericStopping(pb, state::AbstractState; stop_remote::AbstractStopRemoteControl = StopRemoteControl(), main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The one passing the `kwargs` to the `meta`.
  * `GenericStopping(pb, stop_remote::AbstractStopRemoteControl, state::AbstractState; main_stp::AbstractStopping=VoidStopping(), list::AbstractListofStates = VoidListofStates(), user_struct::AbstractDict = Dict(), kwargs...)`    The one passing the `kwargs` to the `meta`.
  * `GenericStopping(pb, x; n_listofstates=, kwargs...)`    The one setting up a default state using x, and initializing the list of states if `n_listofstates>0`.

Note: Metadata can be provided by the user or created with the Stopping        constructor via kwargs. If a specific StoppingMeta is given and        kwargs are provided, the kwargs have priority.

Examples:  `GenericStopping(pb, GenericState(ones(2)), rtol = 1e-1)`

Besides optimality conditions, we consider classical emergency exit:

  * domain error        (for instance: NaN in x)
  * unbounded problem   (not implemented)
  * unbounded x         (x is too large)
  * tired problem       (time limit attained)
  * resources exhausted (not implemented)
  * stalled problem     (not implemented)
  * iteration limit     (maximum number of iteration (i.e. nb of stop) attained)
  * main_pb limit       (tired or resources of main problem exhausted)

There is an additional default constructor which creates a Stopping with a default State.

`GenericStopping(:: Any, :: Union{Number, AbstractVector}; kwargs...)`

Note: Keywords arguments are forwarded to the classical constructor.

Examples:  `GenericStopping(pb, x0, rtol = 1e-1)`
