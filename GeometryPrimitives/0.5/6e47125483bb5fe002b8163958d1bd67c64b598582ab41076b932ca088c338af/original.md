A K-D tree of shapes in `K` dimensions.

This is a binary tree.  Each node in the tree divides space along coordinate `ix` into shapes that overlap the region `≤ x` and `≥ x`. The leaves of the tree are just a list of shapes `s`.

This implementation is a little different from a standard K-D tree, because a given shape may be in both branches of the tree.  (Normally, K-D trees are used for nearest-neighbor searches for a list of *points*, not shapes of nonzero size.)
