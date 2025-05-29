```julia
resetVariableAllInitializations!(fgl)

```

Reset initialization flag on all variables in `::AbstractDFG`.

Notes

  * Numerical values remain, but inference will overwrite since init flags are now `false`.
