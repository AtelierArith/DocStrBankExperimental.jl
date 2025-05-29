```
tess_loaded_languages(
    inst::TessInst
)::Union{Vector{String}, Nothing}
```

Get the the list of languages loaded into the OCR engine.  Returns `nothing` if there was an error.

**Arguments:**

| T   | Name | Default | Description                             |
|:--- |:---- |:------- |:--------------------------------------- |
| R   | inst |         | The instance to get the languages from. |

**Details:**

This method returns the language loaded into the Tesseract engine.  Some language files will load additional languages.  Unlike `tess_initialized_languages()` this method will return all the loaded languages not just the ones it was told to load by the client.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+spa")
true

julia> instance = TessInst("eng+spa")
Allocated Tesseract instance.

julia> tess_loaded_languages(instance)
2-element Vector{String}:
 "eng"
 "spa"
```

See also: [`tess_init`](@ref)
