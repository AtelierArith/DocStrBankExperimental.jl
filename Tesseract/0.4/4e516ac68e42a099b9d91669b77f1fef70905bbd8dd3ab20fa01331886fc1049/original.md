```
tess_initialized_languages(
    inst::TessInst
)::Union{String, Nothing}
```

Retrieve the last initialized language(s).  Returns `nothing` if there was an error.

**Arguments:**

| T   | Name | Default | Description                             |
|:--- |:---- |:------- |:--------------------------------------- |
| R   | inst |         | The instance to get the languages from. |

**Details:**

This method returns the language string provided in the last `tess_init()` call.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.

julia> tess_initialized_languages(instance)
"eng+fra"
```

See also: [`tess_init`](@ref)
