```
BIC(results, dropfirst)
```

Computing the Bayes information criterion.

  * `results`: Result from fitting a count data model.
  * `dropfirst`: Can be used to exclude the first observations from computation.

# Examples

```julia-repl
BIC(res1, 2) # res1: Results from INARCH(1) fit
BIC(res2)    # res2: Results from INARCH(2) fit
```
