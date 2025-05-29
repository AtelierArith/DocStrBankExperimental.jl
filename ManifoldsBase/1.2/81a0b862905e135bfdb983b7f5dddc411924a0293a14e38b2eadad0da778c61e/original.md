```
CompnentError{I,E} <: Exception
```

Store an error that occured in a component, where the additional `index` is stored.

# Fields

  * `index::I` index where the error occured`
  * `error::E` error that occured.
