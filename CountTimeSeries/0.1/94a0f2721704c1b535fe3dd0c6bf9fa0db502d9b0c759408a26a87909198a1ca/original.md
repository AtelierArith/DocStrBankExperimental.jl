```
HQIC(results, dropfirst)
```

Computing the Hannan-Quinn information criterion.

  * `results`: Result from fitting a count data model.
  * `dropfirst`: Can be used to exclude the first observations from computation.

# Examples

```julia-repl
HQIC(res1, 2) # res1: Results from INARCH(1) fit
HQIC(res2)    # res2: Results from INARCH(2) fit
```
