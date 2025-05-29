```
abstract type ParameterPath{OUT} end
```

An indexable type that returns something of type `OUT`. The index can have a lot of complexity, e.g.: A dictionary expansion and a function together determine a platform parameter that leads to a expansion with a smaller error, but more degrees of freedom.
