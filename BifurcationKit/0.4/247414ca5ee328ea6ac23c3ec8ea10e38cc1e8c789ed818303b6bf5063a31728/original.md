```julia
struct DefCont{Tdo, Talg, Tps, Tas, Tud, Tk} <: BifurcationKit.AbstractContinuationAlgorithm
```

Structure which holds the parameters specific to Deflated continuation.

# Fields

  * `deflation_operator::Any`: Deflation operator, `::DeflationOperator` Default: nothing
  * `alg::Any`: Used as a predictor, `::AbstractContinuationAlgorithm`. For example `PALC()`, `Natural()`,... Default: PALC()
  * `max_branches::Int64`: maximum number of (active) branches to be computed Default: 100
  * `seek_every_step::Int64`: whether to seek new (deflated) solution at every step Default: 1
  * `max_iter_defop::Int64`: maximum number of deflated Newton iterations Default: 5
  * `perturb_solution::Any`: perturb function Default: _perturbSolution
  * `accept_solution::Any`: accept (solution) function Default: _acceptSolution
  * `update_deflation_op::Any`: function to update the deflation operator, ie pushing new solutions Default: _updateDeflationOp
  * `jacobian::Any`: jacobian for deflated newton. Can be `DeflatedProblemCustomLS()`, or `Val(:autodiff)`, `Val(:fullIterative)` Default: DeflatedProblemCustomLS()
