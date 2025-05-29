```
PopMember(t::AbstractExpression{T}, cost::L, loss::L)
```

Create a population member with a birth date at the current time. The type of the `Node` may be different from the type of the cost and loss.

# Arguments

  * `t::AbstractExpression{T}`: The tree for the population member.
  * `cost::L`: The cost (normalized to a baseline, and offset by a complexity penalty)
  * `loss::L`: The raw loss to assign.
