```
MutationResult{N<:AbstractExpression,P<:PopMember}
```

Represents the result of a mutation operation in the genetic programming algorithm. This struct is used to return values from `mutate!` functions.

# Fields

  * `tree::Union{N, Nothing}`: The mutated expression tree, if applicable. Either `tree` or `member` must be set, but not both.
  * `member::Union{P, Nothing}`: The mutated population member, if applicable. Either `member` or `tree` must be set, but not both.
  * `num_evals::Float64`: The number of evaluations performed during the mutation, which is automatically set to `0.0`. Only used for things like `optimize`.
  * `return_immediately::Bool`: If `true`, the mutation process should return immediately, bypassing further checks, used for things like `simplify` or `optimize` where you already know the loss value of the result.

# Usage

This struct encapsulates the result of a mutation operation. Either a new expression tree or a new population member is returned, but not both.

Return the `member` if you want to return immediately, and have computed the loss value as part of the mutation.
