```
bindImputations(
    mids1::Mids,
    mids2::Mids
    )
```

Combines two `Mids` objects into one. The two objects must have been created from the same dataset, with the same imputation methods, predictor matrix, visit sequence and number of iterations. The numbers of imputations can be different.
