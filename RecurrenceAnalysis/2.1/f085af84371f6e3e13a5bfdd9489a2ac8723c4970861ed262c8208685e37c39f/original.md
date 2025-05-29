```
nmprt(R[; lmin=2, theiler])
```

Calculate the number of the most probable recurrence time (NMPRT), ruling out the lines shorter than `lmin` (2 by default) and all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).

This number indicates how many times the system has recurred using the recurrence time that appears most frequently, i.e it is the maximum value of the histogram of recurrence times [1].

## References

[1] : E.J. Ngamga *et al.* "Recurrence analysis of strange nonchaotic dynamics", *Physical Review E*, 75(3), 036222(1-8) (2007) [DOI:10.1103/physreve.75.036222](https://doi.org/10.1103/physreve.75.036222)
