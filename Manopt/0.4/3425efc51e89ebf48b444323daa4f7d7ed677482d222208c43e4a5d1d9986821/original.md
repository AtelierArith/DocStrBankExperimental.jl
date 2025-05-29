```
ArmijoLinesearch <: Linesearch
```

A functor representing Armijo line search including the last runs state string the last stepsize.

# Fields

  * `initial_stepsize`:              (`1.0`) and initial step size
  * `retraction_method`:             (`default_retraction_method(M)`) the retraction to use
  * `contraction_factor`:            (`0.95`) exponent for line search reduction
  * `sufficient_decrease`:           (`0.1`) gain within Armijo's rule
  * `last_stepsize`:                 (`initialstepsize`) the last step size to start the search with
  * `initial_guess`:                 (`(p,s,i,l) -> l`)  based on a [`AbstractManoptProblem`](@ref) `p`, [`AbstractManoptSolverState`](@ref) `s` and a current iterate `i` and a last step size `l`, this returns an initial guess. The default uses the last obtained stepsize
  * `additional_decrease_condition`: (`(M,p) -> true`) specify a condition a new point has to additionally fulfill. The default accepts all points.
  * `additional_increase_condition`: (`(M,p) -> true`) specify a condtion that additionally to checking a valid increase has to be fulfilled. The default accepts all points.

as well as for internal use

  * `candidate_point`:           (`allocate_result(M, rand)`) to store an interim result

Furthermore the following fields act as safeguards

  * `stop_when_stepsize_less`:    (`0.0`) smallest stepsize when to stop (the last one before is taken)
  * `stop_when_stepsize_exceeds`: ([`max_stepsize`](@ref)`(M, p)`) largest stepsize when to stop.
  * `stop_increasing_at_step`:    (`100`) last step to increase the stepsize (phase 1),
  * `stop_decreasing_at_step`:    (`1000`) last step size to decrease the stepsize (phase 2),

Pass `:Messages` to a `debug=` to see `@info`s when these happen.

# Constructor

```
ArmijoLinesearch(M=DefaultManifold())
```

with the fields keyword arguments and the retraction is set to the default retraction on `M`.

The constructors return the functor to perform Armijo line search, where

```
(a::ArmijoLinesearch)(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, i)
```

of a [`AbstractManoptProblem`](@ref) `amp`, [`AbstractManoptSolverState`](@ref) `ams` and a current iterate `i` with keywords.

## Keyword arguments

  * `candidate_point`: (`allocate_result(M, rand)`) to pass memory for the candidate point
  * `η`:               (`-get_gradient(mp, get_iterate(s));`) the search direction to use,

by default the steepest descent direction.
