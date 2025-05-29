```
NonIndexedChildren <: ChildIndexing
```

Indicates that the object returned by `children(n)` where `n` is a tree node is not necessarily indexable. This trait applies to any tree which cannot guarantee indexable children in all cases, regardless of whether the tree is indexable in special cases.  For example, `Array` has this trait even though there is a large class of indexable trees consisting of arrays.
