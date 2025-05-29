# Inversion for 2D pulse sequences:

```
invert(seq, x_direct, x_indirect, Data; lims1, lims2, alpha, solver, normalize)
```

This function will build a kernel and use it to perform an inversion using the algorithm of your choice. The output is an `inv_out_2D` structure.

Necessary (positional) arguments:

  * `seq` is the 2D pulse sequence (e.g. IRCPMG)
  * `x_direct` is the direct dimension acquisition parameter (e.g. the times when you aquire CPMG echoes).
  * `x_indirect` is the indirect dimension acquisition parameter (e.g. all the delay times τ in your IR sequence).
  * `Data` is the 2D data matrix of complex data.

Optional (keyword) arguments:

  * `lims1` determines the output "range" of the inversion in the direct dimension (e.g. T₂ times in IRCPMG)
  * `lims2` determines the output "range" of the inversion in the indirect dimension (e.g. T₁ times in IRCPMG)

In both cases above, you can use a tuple specifying the limits of the range, or a vector of values, same as the `lims` argument in the 1D inversion.

  * `alpha` determines the smoothing term. Use a real number for a fixed alpha.  No selection will lead to automatically determining alpha through the default method, which is `gcv`.
  * `solver` is the algorithm used to do the inversion math. Default is `brd`.
  * `normalize` will normalize `Data` to 1 at the max value of `Data`. Default is `true`.
