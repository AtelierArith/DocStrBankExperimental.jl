```
json = modelToJSON(model; expressionsAsStrings=true)
```

Encodes a model as JSON. Expressions can be stored as strings or as ASTs.

  * `model`: model (declarations and equations)
  * `expressionsAsStrings`: Julia expressions stored as strings or Expr struct stored as dictionary
  * `return JSON string for the model`
