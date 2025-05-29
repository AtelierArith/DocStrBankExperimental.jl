```
Optional(T|subcon, [default = nothing]) -> Construct{Union{T, TV}}
Optional{TU}(T|subcon, [default = nothing]) -> Construct{TU}
```

Optional construct with a `default` value.

# Arguments

  * `TU`: the common type of the construct and the default value.
  * `T<:TU`: the type of the sub construct.
  * `TV<:TU`: the type of the default value.
  * `subcon::Construct{T}`: the sub construct.
  * `default::TV`: the default value.
