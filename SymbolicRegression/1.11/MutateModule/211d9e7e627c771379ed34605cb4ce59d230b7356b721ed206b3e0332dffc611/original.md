```
condition_mutation_weights!(weights::AbstractMutationWeights, member::PopMember, options::AbstractOptions, curmaxsize::Int)
```

Adjusts the mutation weights based on the properties of the current member and options.

This function modifies the mutation weights to ensure that the mutations applied to the member are appropriate given its current state and the provided options. It can be overloaded to customize the behavior for different types of expressions or members.

Note that the weights were already copied, so you don't need to worry about mutation.

# Arguments

  * `weights::AbstractMutationWeights`: The mutation weights to be adjusted.
  * `member::PopMember`: The current population member being mutated.
  * `options::AbstractOptions`: The options that guide the mutation process.
  * `curmaxsize::Int`: The current maximum size constraint for the member's expression tree.
