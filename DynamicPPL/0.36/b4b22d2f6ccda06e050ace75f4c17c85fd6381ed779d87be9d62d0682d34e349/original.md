```
extract_priors(model::Model, varinfo::AbstractVarInfo)
```

Extract the priors from a model.

This is done by evaluating the model at the values present in `varinfo` and recording the distributions that are present at each tilde statement.
