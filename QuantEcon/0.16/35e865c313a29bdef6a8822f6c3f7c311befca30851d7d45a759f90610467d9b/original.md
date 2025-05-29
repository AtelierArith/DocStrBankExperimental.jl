```
is_stable(A)
```

General function for testing for stability of matrix $A$. Just checks that eigenvalues are less than 1 in absolute value.

# Arguments

  * `A::Matrix` The matrix we want to check

# Returns

  * `stable::Bool` Whether or not the matrix is stable
