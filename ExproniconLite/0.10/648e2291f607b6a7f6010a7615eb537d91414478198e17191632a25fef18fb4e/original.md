```
mutable struct JLField <: JLExpr
JLField(;kw...)
```

Type describes a Julia field in a Julia struct.

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

The only required keyword argument for the constructor is `name`, the rest are all optional.

  * `name::Symbol`: the name of the field.
  * `type`: the type of the field.
  * `isconst`: if the field is annotated with `const`.
  * `line::LineNumberNode`: a `LineNumberNode` to indicate the line information.
  * `doc::String`: the docstring of this definition.
