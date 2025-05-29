```
currentplot([fig::Figure])
```

Get the "current plot", i.e. the target of the next plotting operations in the (optionally) given figure `fig`.

If no figure is given, the "current figure" is used (cf. [`gcf`](@ref)).
