```
abstract type Transformation
```

The `Transformation` supertype defines a simple interface for performing transformations. Subtypes should be able to apply a coordinate system transformation on the correct data types by overloading the call method, and usually would have the corresponding inverse transformation defined by `Base.inv()`. Efficient compositions can optionally be defined by `compose()` (equivalently `∘`).
