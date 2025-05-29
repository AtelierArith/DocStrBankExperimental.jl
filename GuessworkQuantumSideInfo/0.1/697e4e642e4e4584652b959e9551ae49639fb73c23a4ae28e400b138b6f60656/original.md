```
guesswork(
    p::AbstractVector{T},
    ρBs::AbstractVector{<:AbstractMatrix};
    solver,
    K::Integer = length(p),
    c = T[1:K..., 5_000],
    dual::Bool = false,
    remove_repetition::Bool = true,
    povm_outcomes = make_povm_outcomes(length(p), K, remove_repetition),
    verbose::Bool = true,
)
```

Computes the guesswork for the c-q state specified by a probability vector `p`, giving the distribution `X`, and `ρBs`, giving the associated quantum states.

The keyword arguments are as follows:

  * `solver` is the only required keyword argument; an SDP solver such as SCS or MOSEK must be passed.
  * `K` corresponds to the maximum number of allowed guesses. The number of variables in the primal SDP (and the number of constraints in the dual SDP) scales as `length(p)^K`.
  * `c` may be given a custom cost vector. If `K < length(p)`, then `c` should be of length `K+1`. The last entry, `c[K+1]`, corresponds to the cost of not guessing the correct answer within `K` guesses.
  * `dual` is a boolean variable indicating whether the primal or dual optimization problem should be solved.
  * `remove_repetition` is a boolean variable defaulting to true, indicating whether repeated guesses of the same value should be removed; as long as `c` is increasing, this decreases the size of the SDP without affecting the optimal value.
  * `povm_outcomes` should be an iterator (or vector) corresponding to the possible guessing orders. This defaults to all subsets of length `K` of `1:length(p)` without repetition.
  * `verbose` is a boolean which indicates if warnings should be printed when the problem is not solved optimally.
