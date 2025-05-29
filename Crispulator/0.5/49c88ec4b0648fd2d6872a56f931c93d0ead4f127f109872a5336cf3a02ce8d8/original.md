```julia
select(setup, cells, cell_phenotypes, guides; debug)

```

Given `cells`, a vector of integers, and `guides`, a vector of barcodes, performs simulated FACS sorting of the cells into `bins` with the given cutoffs. `σ` refers to the spread of the phenotype during the FACS screen.
