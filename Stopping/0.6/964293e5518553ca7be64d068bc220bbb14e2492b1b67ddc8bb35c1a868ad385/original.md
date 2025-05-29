Type: StoppingMeta

Methods: no methods.

Attributes:

  * `atol`: absolute tolerance.
  * `rtol`: relative tolerance.
  * `optimality0`: optimality score at the initial guess.
  * `tol_check`: Function of `atol`, `rtol` and `optimality0` testing a score to zero.
  * `tol_check_neg`: Function of `atol`, `rtol` and `optimality0` testing a score to zero.
  * `check_pos`: pre-allocation for positive tolerance
  * `check_neg`: pre-allocation for negative tolerance
  * `recomp_tol`: true if tolerances are updated
  * `optimality_check`: a stopping criterion via an admissibility function
  * `unbounded_threshold`: threshold for unboundedness of the problem.
  * `unbounded_x`: threshold for unboundedness of the iterate.
  * `max_f`: maximum number of function (and derivatives) evaluations.
  * `max_cntrs`: Dict contains the maximum number of evaluations
  * `max_eval`:  maximum number of function (and derivatives) evaluations.
  * `max_iter`: threshold on the number of stop! call/number of iteration.
  * `max_time`: time limit to let the algorithm run.
  * `nb_of_stop`: keep track of the number of stop! call/iteration.
  * `start_time`: keep track of the time at the beginning.
  * `fail_sub_pb`: status.
  * `unbounded`: status.
  * `unbounded_pb`: status.
  * `tired`: status.
  * `stalled`: status.
  * `iteration_limit`: status.
  * `resources`: status.
  * `optimal`: status.
  * `infeasible`: status.
  * `main_pb`: status.
  * `domainerror`: status.
  * `suboptimal`: status.
  * `stopbyuser`: status.
  * `exception`: status.
  * `meta_user_struct`:  Any
  * `user_check_func!`: Function (AbstractStopping, Bool) -> callback.

`StoppingMeta(;atol :: Number = 1.0e-6, rtol :: Number = 1.0e-15, optimality0 :: Number = 1.0, tol_check :: Function = (atol,rtol,opt0) -> max(atol,rtol*opt0), tol_check_neg :: Function = (atol,rtol,opt0) -> -max(atol,rtol*opt0), unbounded_threshold :: Number = 1.0e50, unbounded_x :: Number = 1.0e50, max_f :: Int = typemax(Int), max_eval :: Int = 20000, max_iter :: Int = 5000, max_time :: Number = 300.0, start_time :: Float64 = NaN, meta_user_struct :: Any = nothing, kwargs...)`

an alternative with constant tolerances:

`StoppingMeta(tol_check :: T, tol_check_neg :: T;atol :: Number = 1.0e-6, rtol :: Number = 1.0e-15, optimality0 :: Number = 1.0, unbounded_threshold :: Number = 1.0e50, unbounded_x :: Number = 1.0e50, max_f :: Int = typemax(Int), max_eval :: Int = 20000, max_iter :: Int = 5000, max_time :: Number = 300.0, start_time :: Float64 = NaN, meta_user_struct :: Any = nothing, kwargs...)`

Note:

  * It is a mutable struct, therefore we can modify elements of a `StoppingMeta`.
  * The `nb_of_stop` is incremented everytime `stop!` or `update_and_stop!` is called
  * The `optimality0` is modified once at the beginning of the algorithm (`start!`)
  * The `start_time` is modified once at the beginning of the algorithm (`start!`)     if not precised before.
  * The different status: `fail_sub_pb`, `unbounded`, `unbounded_pb`, `tired`, `stalled`,     `iteration_limit`, `resources`, `optimal`, `main_pb`, `domainerror`, `suboptimal`, `infeasible`
  * `fail_sub_pb`, `suboptimal`, and `infeasible` are modified by the algorithm.
  * `optimality_check` takes two inputs (`AbstractNLPModel`, `NLPAtX`)

and returns a `Number` or an `AbstractVector` to be compared to `0`.

  * `optimality_check` does not necessarily fill in the State.

Examples: `StoppingMeta()`, `StoppingMeta(1., -1.)`
