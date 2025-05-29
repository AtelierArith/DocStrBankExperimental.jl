```
@def_pprint_atomic [to_string=nothing] [mime_types=nothing] [generic_mime=false] T
```

Registers type `T` as an atomic type (i.e., one with no subfields nor subelements) and defines `custom_tile(x::T, mime::MIME{S}) = to_string(x)` for each `mime` type. 

# Arguments

  * `to_string=nothing`: Function expression that returns the string representation of `x`. Defaults to `Base.string` if not provided.
  * `mime_types=nothing`: The `MIME` types to generate. If this value is the empty string, no mime types will be generated. If this value is a non-empty `String` or a `vect` or `tuple` expression of `String`s, these mime types will be used when generating code. Otherwise, if this value is `nothing`, the code generated will use the mime types previously registered with `@mime_type.`
  * `generic_mime::Bool=false`: If `true`, ignores `mime_types` input and use a generic (untemplated) MIME type for all code generation.
