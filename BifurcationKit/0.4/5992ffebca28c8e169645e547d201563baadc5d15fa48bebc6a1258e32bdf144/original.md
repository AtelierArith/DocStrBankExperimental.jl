```julia
hopf_normal_form(prob, pt, ls; verbose, autodiff, L)

```

Compute the Hopf normal form.

# Arguments

  * `prob::AbstractBifurcationProblem` bifurcation problem
  * `pt::Hopf` Hopf bifurcation point
  * `ls` linear solver

# Optional arguments

  * `verbose` bool to print information
  * `L` jacobian
