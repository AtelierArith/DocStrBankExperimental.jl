```
print_results(m::IB, disp_thres = 0.1)
```

Displays the clustering of data for an optimized input model 'm'.

Since the IB algorithm is not deterministic, some probabilities in the clustering matrix 'm.qt*x' are non-zero. For ease of readability, every probability under 'disp*thres' is displayed as 0, everything else as 1. The result is a 2D matrix where the rows represent the clusters and the column the initial categories. The 1 tell to which cluster which category belongs. If several 1 are present for a single category, it means that the optimization wasn't able to assign a single cluster to this category for the chosen β value. You might try a diffent β, or use the DIB variant of the algorithm.
