```
reset_data!(nlp)
```

Reset model data if appropriate. This method should be overloaded if a subtype of `AbstractNLPModel` contains data that should be reset, such as a quasi-Newton linear operator.
