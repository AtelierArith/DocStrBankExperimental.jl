```
cm""
```

A string macro for markdown text that implements standard string interpolation. Returns a parsed markdown AST with the values of the interpolation expressions embedded in the AST.

```julia
value = "interpolated"
cm"Some *$(value)* text."
```

The default syntax rules used for parsing are:

  * `AdmonitionRule`
  * `AttributeRule`
  * `AutoIdentifierRule`
  * `CitationRule`
  * `FootnoteRule`
  * `MathRule`
  * `RawContentRule`
  * `TableRule`
  * `TypographyRule`

which matches closely with the default syntax supported in `Markdown.@md_str`.

!!! info
    The `DollarMathRule` is not enabled since it conflicts with the interpolation syntax. Use double backticks and `math` language literal blocks for maths that is provided by the `MathRule`.


A custom `Parser` can be invoked when using `cm""` by providing a suffix to the macro call, for example:

```julia
more = "more"
cm"Some **$(uppercase(more))** text."none
```

where the suffixed `none` will invoke a basic `Parser` with no additional syntax rules `enabled!`. To use your own custom parser, for example to only enable the `TypographyRule`, you can suffix the call with a named function from the current module's global scope that returns the `Parser` object with the required rules enabled:

```julia
custom() = enable!(Parser(), TypographyRule())
```

It can then be used as

```julia
str = "custom"
cm"A '$(titlecase(str))' parser..."custom
```
