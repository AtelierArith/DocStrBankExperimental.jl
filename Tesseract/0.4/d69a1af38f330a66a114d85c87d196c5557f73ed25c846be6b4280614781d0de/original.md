```
tess_available_languages(
    inst::TessInst
)::Union{Vector{String}, Nothing}
```

Get the list of available languages that can be loaded.  Returns `nothing` if there was an error.

**Arguments:**

| T   | Name | Default | Description                                        |
|:--- |:---- |:------- |:-------------------------------------------------- |
| R   | inst |         | The instance to query for the available languages. |

**Details:**

Get the list of languages that can be used in the tess*init() function.  This method only returns something AFTER `tess*init()`` has been called.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra+spa")
true

julia> instance = TessInst("eng")
Allocated Tesseract instance.

julia> tess_available_languages(instance)
3-element Vector{String}:
 "eng"
 "fra"
 "spa"
```

See also: [`tess_init`](@ref), [`update_languages`](@ref), [`download_languages`](@ref)
