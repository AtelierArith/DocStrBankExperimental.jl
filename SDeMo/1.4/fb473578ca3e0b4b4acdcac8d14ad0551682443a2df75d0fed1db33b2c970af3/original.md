```
VariableSelectionStrategy
```

This is an abstract type to which all variable selection types belong. The variable selection methods should define a method for `variables!`, whose first argument is a model, and the second argument is a selection strategy. The third and fourth positional arguments are, respectively, a list of variables to be included, and the folds to use for cross-validation. They can be omitted and would default to no default variables, and k-fold cross-validation.
