```
isredundant(p::Rep, idx::Index; strongly=false)
```

Return a `Bool` indicating whether the element with index `idx` can be removed without changing the polyhedron represented by `p`. If `strongly` is `true`,

  * if `idx` is an H-representation element `h`, it returns `true` only if no V-representation element of `p` is in the hyperplane of `h`.
  * if `idx` is a V-representation element `v`, it returns `true` only if `v` is in the relative interior of `p`.
