```
Poly(n, p, basis, neighbours; doPlot)
```

Generate a random d-dimensional polyform of size n from the percolation distribution at p using the Metropolis algorithm. neighbours is a list of coordinate differences to each respective neighbouring lattice point defined by the lattice and should be sorted clock-wise to improve performance of the connectivity checks during generation. The default mixing time is 2*n^2

# Arguments

```
* `n`: Size of the polyform
* `p`: Percolation factor in [0, 1)
* `basis`: Lattice basis of the polyform
* `neighbours`: List of difference to the respective neighbouring tiles for the current polyform 
* `doPlot`: If a scatter plot visualizing the polyform should be created (only available for 2d-polyforms)
```
