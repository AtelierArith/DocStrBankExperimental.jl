```
add_constraint_entries!(
    sp::AbstractSparsityPattern, ch::ConstraintHandler;
    keep_constrained::Bool = true,
)
```

Add all entries resulting from constraints in the ConstraintHandler `ch` to the sparsity pattern. Note that, since this operation depends on existing entries in the pattern, this function must be called as the *last* step when creating the sparsity pattern.

# Keyword arguments

  * `keep_constrained`: whether or not entries for constrained DoFs should be kept (`keep_constrained = true`) or eliminated (`keep_constrained = false`) from the sparsity pattern.
