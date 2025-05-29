```
productions(tree; search=PreOrderDFS, nonterminal=identity, terminal=identity)
```

Return a vector of (lhs, rhs) productions from a constituency parse tree.

# Arguments

  * `tree`: the tree to search

# Keywords

  * `nonterminal`: a function to call on nonterminal symbols.
  * `terminal`: a function to call on terminal symbols.

# Returns

  * a `Vector` of (lhs, rhs) tuples
