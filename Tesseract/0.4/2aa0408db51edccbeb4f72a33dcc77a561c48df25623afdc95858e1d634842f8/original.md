```
TessParam(
    name::AbstractString,
    value::AbstractString,
    help::AbstractString
)::TessParam{T} where T
```

Construct a new instance of the [`TessParam`](@ref) structure from the provided values.

**Arguments:**

| T   | Name  | Default | Description                                     |
|:--- |:----- |:------- |:----------------------------------------------- |
| R   | name  |         | The name/ID of the parameter.                   |
| R   | value |         | The default value of the parameter as a string. |
| R   | help  |         | Help text about the parameter.                  |

**Details:**

This method looks at the contents of `value` and determines the correct [`TessParam`](@ref) type to create.

See also: [`tess_params_parsed`](@ref)
