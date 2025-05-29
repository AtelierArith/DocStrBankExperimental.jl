```
object_dictionary(model::Model)
```

Return the dictionary that maps the symbol name of a variable, constraint, or expression to the corresponding object.

Objects are registered to a specific symbol in the macros. For example, `@variable(model, x[1:2, 1:2])` registers the array of variables `x` to the symbol `:x`.

This method should be defined for any subtype of `AbstractModel`.
