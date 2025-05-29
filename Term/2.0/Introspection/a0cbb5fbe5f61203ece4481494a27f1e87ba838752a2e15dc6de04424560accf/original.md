```
inspect(T::DataType; documentation::Bool=false, constructors::Bool=true, methods::Bool=true, supertypes::Bool=true)
```

Inspect a `DataType` to show info such as docstring, constructors and methods. Flags can be used to choose the level of detail in the information presented:

  * documentation: show docstring with `termshow`
  * constructors: show `T` constructors
  * methods: show methods using `T` in their signature
  * supertypes: show methods using `T`'s supertypes in their signature
