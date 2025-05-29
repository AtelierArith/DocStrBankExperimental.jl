```
point(method::TreeGP)
```

Returns an in-place expression mutation function that replaces an arbitrary node in the tree by the randomly selected one. Node replacement mutation is similar to bit string mutation in that it randomly changes a point in the individual. To ensure the tree remains legal, the replacement node has the same number of arguments as the node it is replacing [^6].
