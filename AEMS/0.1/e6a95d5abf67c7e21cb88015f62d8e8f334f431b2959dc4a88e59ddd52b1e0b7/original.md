Implements anytime error minimization search (AEMS). Specifically, this is AEMS2, which generally outperforms AEMS1.

Example with some optional arguments:

`AEMSSolver(max_iterations = 100, action_selector = :L)`

Fields:

  * `max_iterations`   Maximum node expansions per action.
  * `max_time`   Maximum time (in seconds) to spend per action.
  * `updater`   Updater used to propagate belief nodes. Defaults to DiscreteUpdater.
  * `lower_bound`   Subtype of `Policy`. Defaults to fixed action policy.
  * `upper_bound`   Subtype of `Policy`. Defaults to FIB policy.
  * `root_manager`   Allowable values are `:clear`, `:belief`, or `:user`.   Defaults to `:clear`.
  * `action_selector`   Allowable values are `:U` or `:L`. Defaults to `:U`
