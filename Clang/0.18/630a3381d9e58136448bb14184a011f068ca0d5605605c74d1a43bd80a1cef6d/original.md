```
parse_header(
    index::Index,
    header::AbstractString,
    args::Vector{String}=[],
    flags=CXTranslationUnit_None,
) -> TranslationUnit
```

Return the TranslationUnit for a given header. This is the main entry point for parsing.

# Arguments

  * `header::AbstractString`: the header file to parse.
  * `index::Index`: CXIndex pointer (pass to avoid re-allocation).
  * `args::Vector{String}`: compiler switches as string array, eg: ["-x", "c++", "-fno-elide-type"].
  * `flags`: bitwise OR of CXTranslationUnit_Flags.

See also [`parse_headers`](@ref).
