```
Forbidden <: AbstractGrammarConstraint
```

This [`AbstractGrammarConstraint`] forbids any subtree that matches the pattern given by `tree` to be generated. A pattern is a tree of [`AbstractRuleNode`](@ref)s.  Such a node can either be a [`RuleNode`](@ref), which contains a rule index corresponding to the  rule index in the [`AbstractGrammar`](@ref) and the appropriate number of children, similar to [`RuleNode`](@ref)s. It can also contain a [`VarNode`](@ref), which contains a single identifier symbol. A [`VarNode`](@ref) can match any subtree, but if there are multiple instances of the same variable in the pattern, the matched subtrees must be identical. Any rule in the domain that makes the match attempt successful is removed.

For example, consider the tree `1(a, 2(b, 3(c, 4))))`:

  * `Forbidden(RuleNode(3, [RuleNode(5), RuleNode(4)]))` forbids `c` to be filled with `5`.
  * `Forbidden(RuleNode(3, [VarNode(:v), RuleNode(4)]))` forbids `c` to be filled, since a [`VarNode`] can    match any rule, thus making the match attempt successful for the entire domain of `c`.    Therefore, this tree invalid.
  * `Forbidden(RuleNode(3, [VarNode(:v), VarNode(:v)]))` forbids `c` to be filled with `4`, since that would    make both assignments to `v` equal, which causes a successful match.
