```
trend(R[; border=10, theiler])
```

Calculate the trend of recurrences in the recurrence matrix `R`.

## Description

The trend is the slope of the linear regression that relates the density of recurrent points in the diagonals parallel to the LOI and the distance between those diagonals and the LOI. It quantifies the degree of system stationarity, such that in recurrence plots where points "fade away" from the central diagonal, the trend will have a negative value.

It is calculated as:

$$
TREND = 10^3\frac{\sum_{d=1+\tau}^{\tilde{N}}\delta[d]\left(RR[d]-\langle RR[d]\rangle\right)}{\sum_{d=1+\tau}^{\tilde{N}}\delta[d]^2}
$$

where $RR[d]$ is the local recurrence rate of the diagonal $d$, $\tau$ is the Theiler window (number of central diagonals that are excluded), $\tilde{N}$ is the number of the outmost diagonal that is included, and $\delta[d]$ is a balanced measure of the distance between that diagonal and the LOI equal to $d-(\tilde{N}+\tau)/2$.

This parameter is expressed in units of variation recurrence rate every 1000 data points, hence the factor $10^3$ in the formula [1].

The 10 outermost diagonals (counting from the corners of the matrix) are excluded by default to avoid "border effects". Use the keyword argument `border` to define a different number of excluded lines, and `theiler` to define the size of the Theiler window (see [`rqa`](@ref) for details).

*Note*: In rectangular cross-recurrence plots (i.e. when the time series that originate them are not of the same length), the limits of the formula for TREND are not clearly defined. For the sake of consistency, this function limits the calculations to the biggest square matrix that contains the LOI.

## References

[1] C.L. Webber & J.P. Zbilut, "Recurrence Quantification Analysis of Nonlinear Dynamical Systems", in: Riley MA & Van Orden GC, *Tutorials in Contemporary Nonlinear Methods for the Behavioral Sciences*, 2005, 26-94. https://www.nsf.gov/pubs/2005/nsf05057/nmbs/nmbs.pdf
