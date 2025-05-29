```
selfmutualinfo(s, τs; kwargs...) → m
```

Calculate the mutual information between the time series `s` and itself delayed by `τ` points for `τ` ∈ `τs`, using an *improvement* of the method outlined by Fraser & Swinney in[^Fraser1986].

## Description

The joint space of `s` and its `τ`-delayed image (`sτ`) is partitioned as a rectangular grid, and the mutual information is computed from the joint and marginal frequencies of `s` and `sτ` in the grid as defined in [1]. The mutual information values are returned in a vector `m` of the same length as `τs`.

If any of the optional keyword parameters is given, the grid will be a homogeneous partition of the space where `s` and `sτ` are defined. The margins of that partition will be divided in a number of bins equal to `nbins`, such that the width of each bin will be `binwidth`, and the range of nonzero values of `s` will be in the centre. If only of those two parameters is given, the other will be automatically calculated to adjust the size of the grid to the area where `s` and `sτ` are nonzero.

If no parameter is given, the space will be partitioned by a recursive bisection algorithm based on the method given in [1].

Notice that the recursive method of [1] evaluates the joint frequencies of `s` and `sτ` in each cell resulting from a partition, and stops when the data points are uniformly distributed across the sub-partitions of the following levels. For performance and stability reasons, the automatic partition method implemented in this function is only used to divide the axes of the grid, using the marginal frequencies of `s`.

[^Fraser1986]: Fraser A.M. & Swinney H.L. "Independent coordinates for strange attractors from mutual information" *Phys. Rev. A 33*(2), 1986, 1134:1140.
