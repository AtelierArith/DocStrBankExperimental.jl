```
geodesic(tree1::T, tree2::T)::Float64 where T<:GeneralNode
```

This function calculates and returns the geodesic distance between two trees.

  * `tree1` : root node of the first tree.
  * `tree2` : root node of the second tree.
  * `verbose`: If set to 'true', prints the common edge and the leaf contribution.

The GTP algorithm computing the geodesic distance is closely adapted from the Java  implementation of that same algorithm by Megan Owen and J. Scott Provan.

(M. Owen and J.S. Provan. A fast algorithm for computing geodesic distances in tree space.  IEEE/ACM Transactions on Computational Biology and Bioinformatics, 8:2-13, 2011.) 
