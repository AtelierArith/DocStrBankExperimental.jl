```
fulldummy(term::CategoricalTerm)
```

Assign "contrasts" that include all indicator columns (dummy variables) and an intercept column.

This will result in an under-determined set of contrasts, which is not a problem in the random effects because of the regularization, or "shrinkage", of the conditional modes.

The interaction of `fulldummy` with complex random effects is subtle and complex with numerous potential edge cases. As we discover these edge cases, we will document and determine their behavior. Until such time, please check the model summary to verify that the expansion is working as you expected. If it is not, please report a use case on GitHub.
