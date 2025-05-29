```
mutate!(
    tree::N,
    member::P,
    ::Val{S},
    mutation_weights::AbstractMutationWeights,
    options::AbstractOptions;
    kws...,
) where {N<:AbstractExpression,P<:PopMember,S}
```

Perform a mutation on the given `tree` and `member` using the specified mutation type `S`. Various `kws` are provided to access other data needed for some mutations.

You may overload this function to handle new mutation types for new `AbstractMutationWeights` types.

# Keywords

  * `temperature`: The temperature parameter for annealing-based mutations.
  * `dataset::Dataset`: The dataset used for scoring.
  * `cost`: The cost of the member before mutation.
  * `loss`: The loss of the member before mutation.
  * `curmaxsize`: The current maximum size constraint, which may be different from `options.maxsize`.
  * `nfeatures`: The number of features in the dataset.
  * `parent_ref`: Reference to the mutated member's parent (only used for logging purposes).
  * `recorder::RecordType`: A recorder to log mutation details.

# Returns

A `MutationResult{N,P}` object containing the mutated tree or member (but not both), the number of evaluations performed, if any, and whether to return immediately from the mutation function, or to let the `next_generation` function handle accepting or rejecting the mutation. For example, a `simplify` operation will not change the loss, so it can always return immediately.
