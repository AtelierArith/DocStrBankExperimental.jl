```
AIC(results, dropfirst)
```

Computing the Akaike information criterion.

  * `results`: Result from fitting a count data model.
  * `dropfirst`: Can be used to exclude the first observations from computation.

# Examples

```julia-repl
AIC(res1, 2) # res1: Results from INARCH(1) fit
AIC(res2)    # res2: Results from INARCH(2) fit
```
