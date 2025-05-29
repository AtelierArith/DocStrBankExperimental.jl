```
show_typst(io, x)
```

Print in Typst format with Julia settings and Typst parameters provided by an `IOContext`.

Implement this function for a custom type to specify its Typst formatting. A setting is a value used in Julia, whose type varies across settings. A parameter is passed directly to a Typst function and must be a [`TypstString`](@ref) with the same name as in Typst, except that dashes are replaced with underscores. Settings each have a default value, whereas the default values of parameters are handled by Typst functions. Some settings, such as `block`, correspond with a parameter but may also be used in Julia.

For additional information on settings and parameters, see also [`context`](@ref) and the [Typst Documentation](https://typst.app/docs/), respectively.

!!! info
    Some types, particularly containers, may call [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref) to format a value, which may use additional settings and parameters.


!!! warning
    This function's methods are incomplete. Please file an issue or create a pull-request for missing methods.


| Type                                            | Settings                                 | Parameters                                              |
|:----------------------------------------------- |:---------------------------------------- |:------------------------------------------------------- |
| `AbstractArray`                                 | `:block`, `:depth`, `:mode`, `:tab_size` | `:delim`, `:gap`                                        |
| `AbstractChar`                                  |                                          |                                                         |
| `AbstractFloat`                                 | `:mode`                                  |                                                         |
| `AbstractMatrix`                                | `:block`, `:depth`, `:mode`, `:tab_size` | `:augment`, `:column_gap`, `:delim`, `:gap`, `:row_gap` |
| `AbstractString`                                |                                          |                                                         |
| `Bool`                                          | `:mode`                                  |                                                         |
| `Complex{Bool}`                                 | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Complex`                                       | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Irrational`                                    | `:mode`                                  |                                                         |
| `Nothing`                                       | `:mode`                                  |                                                         |
| `OrdinalRange{<:Integer, <:Integer}`            | `:mode`                                  |                                                         |
| `Rational`                                      | `:block`, `:mode`, `:parenthesize`       |                                                         |
| `Regex`                                         | `:mode`                                  |                                                         |
| `Signed`                                        | `:mode`                                  |                                                         |
| `StepRangeLen{<:Integer, <:Integer, <:Integer}` | `:mode`                                  |                                                         |
| `Tuple`                                         | `:block`, `:depth`, `:mode`, `:tab_size` | `:delim`, `:gap`                                        |
| `Typst`                                         |                                          |                                                         |
| `TypstString`                                   |                                          |                                                         |
| `TypstText`                                     | `:mode`                                  |                                                         |
| `Unsigned`                                      | `:mode`                                  |                                                         |
| `VersionNumber`                                 | `:mode`                                  |                                                         |
| `Docs.HTML`                                     | `:block`, `:depth`, `:mode`, `:tab_size` |                                                         |
| `Docs.Text`                                     | `:mode`                                  |                                                         |
| `Dates.Date`                                    | `:mode`, `:indent`                       |                                                         |
| `Dates.DateTime`                                | `:mode`, `:indent`                       |                                                         |
| `Dates.Period`                                  | `:mode`, `:indent`                       |                                                         |
| `Dates.Time`                                    | `:mode`, `:indent`                       |                                                         |
