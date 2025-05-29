```
struct MaxSizeBranchCount
```

Reture both the max size of the results and number of branches.

# Fields

  * `size::Int`: The max size of the results.
  * `count::Int`: The number of branches of that size.

# Constructors

  * `MaxSizeBranchCount(size::Int)`: Creates a `MaxSizeBranchCount` with the given size and initializes the count to 1.
  * `MaxSizeBranchCount(size::Int, count::Int)`: Creates a `MaxSizeBranchCount` with the specified size and count.
