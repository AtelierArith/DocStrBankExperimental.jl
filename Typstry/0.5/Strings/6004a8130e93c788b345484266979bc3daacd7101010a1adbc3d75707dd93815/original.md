```
context(x)
```

Provide formatting data for [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref).

Implement this function for a custom type to specify its custom settings and parameters. Passing a value wrapped in [`Typst`](@ref) will `merge!` its custom context with defaults, such that the defaults may be overwritten. To be compatible with merging contexts and constructing an `IOContext`, methods must return an `AbstractDict{Symbol}`.

| Setting         | Default  | Type           | Description                                                                                                                                                                       |
|:--------------- |:-------- |:-------------- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:backticks`    | `3`      | `Int`          | The number of backticks to enclose raw text markup, which may be increased to disambiguiate nested raw text.                                                                      |
| `:block`        | `false`  | `Bool`         | When `:mode => math`, specifies whether the enclosing dollar signs are padded with a space to render the element inline or its own block.                                         |
| `:depth`        | `0`      | `Int`          | The current level of nesting within container types to specify the degree of indentation.                                                                                         |
| `:mode`         | `markup` | [`Mode`](@ref) | The current Typst syntactical context where `code` follows the number sign, `markup` is at the top-level and enclosed in square brackets, and `math` is enclosed in dollar signs. |
| `:parenthesize` | `true`   | `Bool`         | Whether to enclose some mathematical elements in parentheses to specify their operator precedence and avoid ambiguity.                                                            |
| `:tab_size`     | `2`      | `Int`          | The number of spaces used by some elements with multi-line Typst formatting, which is repeated for each level of `depth`                                                          |
