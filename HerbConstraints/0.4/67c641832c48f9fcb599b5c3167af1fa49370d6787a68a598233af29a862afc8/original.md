```
ForbiddenSequence <: AbstractGrammarConstraint
```

This [`AbstractGrammarConstraint`] forbids the given `sequence` of rule nodes. Sequences are strictly vertical and may include gaps. Consider the tree `1{a, 2{b, 3{c, d}}}`:

  * `[2, 3, d]` is a sequence
  * `[1, 3, d]` is a sequence
  * `[3, c, d]` is not a sequence since c and d are siblings (horizontal)

Examples:

  * `ForbiddenSequence([3, 4])` enforces that rule `4` cannot be applied at `c` or `d`.
  * `ForbiddenSequence([1, 2, 4])` enforces that rule `4` cannot be applied at `b`, `c` or `d`.
  * `ForbiddenSequence([1, 4])` enforces that rule `4` cannot be applied anywhere.

If any of the rules in `ignore_if` appears in the sequence, the constraint is ignored. Suppose the forbidden `sequence = [1, 2, 3]` and `ignore_if = [99]` Consider the following paths from the root:

  * `[1, 2, 2, 3]` is forbidden, as the sequence does not contain `99`
  * `[1, 99, 2, 3]` is NOT forbidden, as the sequence does contain `99`
  * `[1, 99, 1, 2, 3]` is forbidden, as there is a subsequence that does not contain `99`
