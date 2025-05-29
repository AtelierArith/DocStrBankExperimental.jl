```
PopMember(
    dataset::Dataset{T,L},
    t::AbstractExpression{T},
    options::AbstractOptions
)
```

Create a population member with a birth date at the current time. Automatically compute the cost for this tree.

# Arguments

  * `dataset::Dataset{T,L}`: The dataset to evaluate the tree on.
  * `t::AbstractExpression{T}`: The tree for the population member.
  * `options::AbstractOptions`: What options to use.
