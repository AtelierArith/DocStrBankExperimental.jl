```
label_components(tf, [connectivity])
label_components(tf, [region])
```

Find the connected components in a binary array `tf`. There are two forms that `connectivity` can take.

(1) It can be a boolean array of the same dimensionality as `tf`, of size 1 or 3 along each dimension. Each entry in the array determines whether a given neighbor is used for connectivity analyses. For example, `connectivity = trues(3,3)` would use 8-connectivity and test all pixels that touch the current one, even the corners.

(2) You can provide a list indicating which dimensions are used to determine connectivity. For example, `region = [1,3]` would not test neighbors along dimension 2 for connectivity. This corresponds to just the nearest neighbors, i.e., 4-connectivity in 2d and 6-connectivity in 3d. The default is `region = 1:ndims(A)`. The output `label` is an integer array, where 0 is used for background pixels, and each connected region gets a different integer index.
