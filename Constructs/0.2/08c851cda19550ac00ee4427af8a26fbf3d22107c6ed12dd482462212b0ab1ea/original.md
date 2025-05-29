```
Validator(T|subcon, validate) -> Validator{T}
```

Create a validator based on the `validate` function.

# Arguments

  * `subcon::Construct{T}`: the underlying construct.
  * `validate`: the validate function. the function should have signature like `(::T; contextkw...)->Bool`.
