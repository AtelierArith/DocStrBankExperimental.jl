```
BicoloredRootedTreeIterator(order::Integer)
```

Iterator over all bi-colored rooted trees of given `order`. The returned trees are views to an internal tree modified during the iteration. If the returned trees shall be stored or modified during the iteration, a `copy` has to be made.
