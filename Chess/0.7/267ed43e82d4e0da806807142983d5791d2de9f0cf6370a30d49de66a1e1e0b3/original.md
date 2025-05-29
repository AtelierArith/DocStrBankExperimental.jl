```
SquareSet
```

A type representing a set of squares on the chess board.

The most common ways of obtaining a square set are:

  * Initializing it with one or more squares, for instance `SquareSet(SQ_D4, SQ_E4, SQ_D5, SQ_E5)`.
  * From one of the predefined square set constants, like `SS_FILE_C` (the squares on the C file) or `SS_RANK_7` (the squares on the 7th rank).
  * By extracting it from a chess board. See the `Board` type for details about this.
  * By performing operations transforming or combining one or more square sets to a new square set.

The union or intersection of two sets can be computed by the functions `union` and `intersect`, or by the corresponding binary operators `∪` and `∩`. The complement of a square set is denoted by the unary `-` operator. The difference between two set is obtained by the `setdiff` function or by the binary `-` operator. Subset relationships can be tested by the `issubset` function or the binary operator `⊆`.

To add or remove a square to a square set, use the `+` or `-` operators with the square set as the left operand and the square as the right operand. To test whether a square set contains a square, use `s in ss` or `s ∈ ss`.
