```
XPRS_TREEMEMORYSAVINGTARGET
```

When the memory used by the branch-and-bound search tree exceeds the limit specified by the TREEMEMORYLIMIT control, the optimizer will try to save memory by writing lower-rated sections of the tree to the tree file. (double)

The target amount of memory to save will be enough to bring memory usage back below the limit, plus enough extra to give the tree room to grow. The `TREEMEMORYSAVINGTARGET` control specifies the extra proportion of the tree's size to try to save; for example, if the tree memory limit is 1000Mb and `TREEMEMORYSAVINGTARGET` is 0.1, when the tree size exceeds 1000Mb the optimizer will try to reduce the tree size to 900Mb. Reducing the value of `TREEMEMORYSAVINGTARGET` will cause less extra nodes of the tree to be written to the tree file, but will result in the memory saving routine being triggered more often (as the tree will have less room in which to grow), which can reduce performance. Increasing the value of `TREEMEMORYSAVINGTARGET` will cause additional, more highly-rated nodes, of the tree to be written to the tree file, which can cause performance issues if these nodes are required later in the solve.

Default value: 0.4

Domain: [0.01,+1.0]
