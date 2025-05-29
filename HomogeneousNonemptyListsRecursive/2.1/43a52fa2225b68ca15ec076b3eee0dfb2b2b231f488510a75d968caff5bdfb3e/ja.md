```
homogeneous_nonempty_list_with_refined_type(::HomogeneousNonemptyListRecursive)
```

Return the argument unchanged. Throws for invalid/malformed arguments. Even though the returned value is identical to the argument, Julia's type inference may have more precise knowledge about the type of the returned value than of the argument.
