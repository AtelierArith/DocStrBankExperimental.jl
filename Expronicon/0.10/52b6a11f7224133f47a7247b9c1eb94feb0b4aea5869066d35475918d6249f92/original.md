```
mutable struct JLKwField <: JLExpr
```

Type describes a Julia field that can have a default value in a Julia struct.

```
JLKwField(;kw...)
```

Create a `JLKwField` instance.

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

The only required keyword argument for the constructor is `name`, the rest are all optional.

  * `name::Symbol`: the name of the field.
  * `type`: the type of the field.
  * `isconst`: if the field is annotated with `const`.
  * `default`: default value of the field, default is [`no_default`](@ref).
  * `line::LineNumberNode`: a `LineNumberNode` to indicate the line information.
  * `doc::String`: the docstring of this definition.
