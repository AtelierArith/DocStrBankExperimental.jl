```
recurrencerate(R[; theiler])
```

Calculate the recurrence rate of the recurrence matrix `R`.

## Description

The recurrence rate is calculated as:

$$
RR = \frac{1}{S} \sum R
$$

where $S$ is the size of `R` or the region of `R` with potential recurrent points. There is not a unique definition of that denominator, which is defined as the full size of the matrix in many sources (e.g. [1]), whereas in others it is adjusted to remove the points of the LOI when they are excluded from the count [2,3].

For matrices of type `RecurrenceMatrix` or `JointRecurrenceMatrix`, where the points around the central diagonal are usually excluded, the denominator is adjusted to the size of the matrix outside the Theiler window (by default equal to the LOI, and adjustable with the keyword argument `theiler`; see [`rqa`](@ref) for details). For matrices of type `CrossRecurrenceMatrix`, where normally all points are analyzed, the denominator is always the full size of the matrix, regardless of the Theiler window that might be defined (none by default).

*Hint*: to reproduce the calculations done following the formulas that use the full size of the matrix in the denominator, use `CrossRecurrenceMatrix(s,s,ε)` to define the recurrence matrix, instead of `RecurrenceMatrix(s,ε)`, setting `theiler=1` (or `theiler=n` in general) to explicitly exclude the LOI or other diagonals around it.

## References

[1] : N. Marwan *et al.*, "Recurrence plots for the analysis of complex systems", *Phys. Reports 438*(5-6), 237-329 (2007). [DOI:10.1016/j.physrep.2006.11.001](https://doi.org/10.1016/j.physrep.2006.11.001)

[2] : C.L. Webber & J.P. Zbilut, "Recurrence Quantification Analysis of Nonlinear Dynamical Systems", in: Riley MA & Van Orden GC, Tutorials in Contemporary Nonlinear Methods for the Behavioral Sciences, 26-94 (2005). URL: https://www.nsf.gov/pubs/2005/nsf05057/nmbs/nmbs.pdf

[3] : N. Marwan & C.L. Webber, "Mathematical and computational foundations of recurrence quantifications", in: Webber, C.L. & N. Marwan (eds.), *Recurrence Quantification Analysis. Theory and Best Practices*, Springer, pp. 3-43 (2015).
