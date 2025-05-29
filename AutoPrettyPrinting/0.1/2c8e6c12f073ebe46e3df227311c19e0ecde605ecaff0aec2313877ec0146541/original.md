```
@custom_tile [mime_types=nothing] [generic_mime=false] [base_show=false] T => custom_tile_expr
```

Creates custom tile method definitions for type `T` and optionally provided `mime_types` using `custom_tile_expr` as the function's body. 

# Arguments

  * `mime_types=nothing`: The `MIME` types to generate. If this value is the empty string, no mime types will be generated. If this value is a non-empty `String` or a `vect` or `tuple` expression of `String`s, these mime types will be used when generating code. Otherwise, if this value is `nothing`, the code generated will use the mime types previously registered with `@mime_type.`
  * `generic_mime::Bool=false`: If `true`, ignores `mime_types` input and use a generic (untemplated) MIME type for all code generation.
  * `base_show::Bool=false`: If `true`, will define `Base.show(io::IO, ::MIME(mime), ::T)` for each `mime` in `mime_types`
  * `custom_tile_expr`: Expression to be used for the body of the `custom_tile` method. If this value is a `block` expression, it should contain a `_obj_` placeholder to indicate the object of type `T` and a `_mime_` placeholder to indicate the mime type. Otherwise, it can be a function definition expression of the form `(object, mime_type)->expr`.
