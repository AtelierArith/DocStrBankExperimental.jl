```
subtree(method::TreeGP; growth::Real = 0.0)
```

Returns an in-place expression mutation function that performs mutation of an arbitrary expression subtree with a randomly generated one [^5].

Parameters:

  * `growth`: Growth restriction on the offspring in comparison to the parent.           The offspring cannot be more than `growth`% deeper than its parent.  (default: `0.0`)
