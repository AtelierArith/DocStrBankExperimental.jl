```
with(
    mids::Mids,
    func::Function
    )
```

Conducts repeated analyses of a multiply imputed dataset (`Mids`).

The function takes two arguments: firstly the `Mids` object itself, then a function (`func`). The function should take the form `data -> analysisFunction(arguments, data, moreArguments...)`, where `data` represents the position of the data argument in the function.

For example: `with(mids, data -> lm(@formula(y ~ x1 + x2), data))`
