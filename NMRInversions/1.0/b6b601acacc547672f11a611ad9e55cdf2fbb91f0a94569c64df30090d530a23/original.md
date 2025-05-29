# Generating a kernel for a 2D inversion

```
create_kernel(seq, x_direct, x_indirect, X_direct, X_indirect, Data)
```

  * `seq` is the 2D pulse sequence (e.g. IRCPMG)
  * `x_direct` is the direct dimension acquisition parameter (e.g. the times when you aquire CPMG echoes).
  * `x_indirect` is the indirect dimension acquisition parameter (e.g. all the delay times τ in your IR sequence).
  * `X_direct` is output "range" of the inversion in the direct dimension (e.g. T₂ times in IRCPMG)
  * `X_indirect` is output "range" of the inversion in the indirect dimension (e.g. T₁ times in IRCPMG)
  * `Data` is the 2D data matrix of complex data.

The output is an `svd_kernel_struct`
