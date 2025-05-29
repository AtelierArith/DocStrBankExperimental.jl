```
@def_pprint [properties=nothing] [mime_types=nothing] [generic_mime=false] [base_show=false] T
```

Auto generates pretty printing methods for type `T` and optionally provided `mime_types`. 

# Arguments

  * `properties=nothing`: Either a `Symbol` or a `vect` expression of `Symbol`s corresponding to the properties to use from `x::T`. Will default to using the fieldnames of `x` if unspecified
  * `mime_types=nothing`: The `MIME` types to generate. If this value is the empty string, no mime types will be generated. If this value is a non-empty `String` or a `vect` or `tuple` expression of `String`s, these mime types will be used when generating code. Otherwise, if this value is `nothing`, the code generated will use the mime types previously registered with `@mime_type.`
  * `generic_mime::Bool=false`: If `true`, ignores `mime_types` input and use a generic (untemplated) MIME type for all code generation.
  * `base_show::Bool=false`: If `true`, will define `Base.show(io::IO, ::MIME(mime), ::T)` for each `mime` in `mime_types`
