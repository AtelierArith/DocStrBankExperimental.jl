```
frechet_c_compute
```

Compute the exact continuous (monotone) Frechet distance between the two polygons. It should be reasonably fast.

This function is somewhat slower than the approximate versions. Use it only if you really want the exact answer. Consider using frechet*continous*approx instead.

# Details

This works by first computing a very rough approximation, followed by distance senstiave simplification of the curves. It then compute the monotone fr*ve*r distance between the simplified curves, and it combine it to get a distance between the two original cuves. It makre sure the answers are the same, otherwise, it repeates with a finer simplification/approximation till they are equal.

Finally, the algorithm uses the fr*ve*r*with*offests distance between the two simplified curves to comptue a lower bound, and make sure this is equal to the Frechet distance computed. If they are equal, then the upper/lower bounds on the Frechet distance of the two curves are the same, which implies that the computed distance is indeed the desired Frechet distance.

# More details

To really ensure converges, the monotone distance computed between the simplification is computed using refinement, so tha the ve_r distance
