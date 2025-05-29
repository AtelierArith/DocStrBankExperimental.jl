```
Ordered <: AbstractGrammarConstraint
```

A [`AbstractGrammarConstraint`](@ref) that enforces a specific order in [`MatchVar`](@ref)  assignments in the pattern defined by `tree`. Nodes in the pattern can either be a [`RuleNode`](@ref), which contains a rule index corresponding to the  rule index in the [`AbstractGrammar`](@ref) and the appropriate number of children. It can also contain a [`VarNode`](@ref), which contains a single identifier symbol. A [`VarNode`](@ref) can match any subtree.  If there are multiple instances of the same variable in the pattern, the matched subtrees must be identical.

The `order` defines an order between the variable assignments.  For example, if the order is `[x, y]`, the constraint will require  the assignment to `x` to be less than or equal to the assignment to `y`. The order is recursively defined by [`RuleNode`](@ref) indices.  For more information, see [`Base.isless(rn₁::AbstractRuleNode, rn₂::AbstractRuleNode)`](@ref).

For example, consider the tree `1(a, 2(b, 3(c, 4))))`:

  * `Ordered(RuleNode(3, [VarNode(:v), VarNode(:w)]), [:v, :w])` removes every rule    with an index of 5 or greater from the domain of `c`, since that would make the index of the    assignment to `v` greater than the index of the assignment to `w`, violating the order.
  * `Ordered(RuleNode(3, [VarNode(:v), VarNode(:w)]), [:w, :v])` removes every rule    with an index of 4 or less from the domain of `c`, since that would make the index of the    assignment to `v` less than the index of the assignment to `w`, violating the order.
