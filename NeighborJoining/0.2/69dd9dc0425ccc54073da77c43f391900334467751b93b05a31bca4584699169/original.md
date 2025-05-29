```
merges(t::NJClust)
```

extracts the merge list from NJClust object. rowindex is the internal node id,  and each column represents the children nodes.  Leaf nodes are represented by negative integers corresponding to the index in the original distance matrix
