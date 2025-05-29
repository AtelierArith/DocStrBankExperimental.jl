```
reduce(α::DecisionDiagram)
```

Returns the canonical form of the decision diagram α.  A diagram is canonical iff:

  * no two terminals are assigned to the same value
  * no two nodes have are labeled by the same variable and have the same two reduced children low and high with identical ids
