```
ExpectedImprovement(; kwargs...)
```

The expected improvement (EI) acquisition function.

Fitness function must be defined as a part of the problem definition in order to use EI. (See `Fitness`.)

Measures the quality of a potential evaluation point `x` as the expected improvement in best-so-far achieved fitness by evaluating the objective function at `y = f(x)`.

In case of constrained problems, the expected improvement is additionally weighted by the probability of feasibility of `y`. I.e. the probability that `all(cons(y) .> 0.)`.

If the problem is constrained on `y` and no feasible point has been observed yet, then the probability of feasibility alone is returned as the acquisition function.

Rather than using the actual evaluations `(xᵢ,yᵢ)` from the dataset, the best-so-far achieved fitness is calculated as the maximum fitness among the means `̂yᵢ` of the posterior predictive distribution of the model evaluated at `xᵢ`. This is a simple way to handle evaluation noise which may not be suitable for problems with substantial noise. In case of Bayesian Inference, an averaged posterior of the model posterior samples is used for the prediction of `ŷᵢ`.

# Keywords

  * `ϵ_samples::Int`: Controls how many samples are used to approximate EI.       The `ϵ_samples` keyword is *ignored* unless `MAP` model fitter and `NonlinFitness` are used!       In case of `BI` model fitter, the number of samples is instead set equal to the number of posterior samples.       In case of `LinearFitness`, the expected improvement can be calculated analytically.
  * `cons_safe::Bool`: If set to true, the acquisition function `acq(x)` is made 'constraint-safe'       by checking the bounds and constraints during each evaluation.       Set `cons_safe` to `true` if the evaluation of the model at exterior points       may cause errors or nonsensical values.       You may set `cons_safe` to `false` if the evaluation of the model at exterior points       can provide useful information to the acquisition maximizer and does not cause errors.       Defaults to `true`.
