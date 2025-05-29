```
evaluate!(func::Function, eval::AbstractEvaluator, name::Symbol, (ingredients::Symbol...))
```

Define an evaluable called `name`, i.e. a quantity depending on the observable averages `ingredients...`. The function `func` will get the ingredients as parameters and should return the value of the evaluable. Carlo will then perform jackknifing to calculate a bias-corrected result with correct error bars that appears together with the observables in the result file.
