```
machines(N::AbstractNode [, model::Model])
```

List all machines in the ancestor graph of node `N`, optionally restricting to those machines whose corresponding model matches the specifed `model`.

Here two models *match* if they have the same, possibly nested hyperparameters, or, more precisely, if `MLJModelInterface.is_same_except(m1, m2)` is `true`.

See also `MLJModelInterface.is_same_except`.
