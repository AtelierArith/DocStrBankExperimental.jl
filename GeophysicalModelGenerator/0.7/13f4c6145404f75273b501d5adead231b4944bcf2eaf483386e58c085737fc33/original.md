```
Top, Bot = compute_slab_surface(trench::Trench)
```

Computes the (`x`,`z`) coordinates of the slab top, bottom surface using the mid surface of the slab as reference.

# Parameters

  * `trench`          - `Trench` structure that contains the relevant parameters

# Method

It computes it by discretizing the slab surface in `n_seg` segments, and computing the average bending angle (which is a function of the current length of the slab). Next, it compute the coordinates assuming that the trench is at 0.0, and assuming a positive `θ_max` angle.
