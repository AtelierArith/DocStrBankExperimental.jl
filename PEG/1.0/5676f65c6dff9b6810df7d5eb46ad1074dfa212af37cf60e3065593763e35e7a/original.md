```
squash_ast(x)
```

Given an ast returned by a grammar with no semantics, return a simplified version, such that there are no `nothing`s, and no `Any[]`s with exactly zero or one element.
