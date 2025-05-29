```
KFoldValidation(k; shuffle=true, loss=Dict())
```

`k`-fold cross-validation. Optionally, `shuffle` the data, and specify a dictionary with `loss` functions from `LossFunctions.jl` for some of the variables.

## References

  * Geisser, S. 1975. [The predictive sample reuse method with applications](https://www.jstor.org/stable/2285815)
  * Burman, P. 1989. [A comparative study of ordinary cross-validation, v-fold cross-validation and the repeated learning-testing methods](https://www.jstor.org/stable/2336116)
