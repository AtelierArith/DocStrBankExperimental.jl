```
searchtree(pred, tree, bb)
```

Return an iterator that returns indices stores in tree that correspond to objects for which the supplied predicate holds.

`pred` takes an integer an returns true is the corresponding object stored in `tree` collides with the target object. `bb` is a bounding box containing the target. This bounding box is used for effiently excluding entire branches of the tree.
