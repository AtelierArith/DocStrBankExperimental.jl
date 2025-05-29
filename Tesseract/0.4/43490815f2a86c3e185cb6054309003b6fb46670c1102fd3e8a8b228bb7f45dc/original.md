```
tess_init(
    inst::TessInst,
    languages::AbstractString = "eng",
    dataPath::AbstractString = "tessdata"
)::Bool
```

Initialize the instance for the specified language(s).  Returns `false` if there was an error.

**Arguments:**

| T   | Name      | Default    | Description                                      |
|:--- |:--------- |:---------- |:------------------------------------------------ |
| R   | inst      |            | The instance to initialize.                      |
| O   | languages | `eng`      | The language(s) to load.                         |
| O   | dataPath  | `tessdata` | The directory to look for the language files in. |

**Details:**

This method can be called multiple times to reinitialize the langauges to OCR with.  Multiple langagues can be specified by seperating them with a plus.  So if you want english and spanish you could specify "eng+spa".  The language codes are (usually) the [ISO 639-3](https://en.wikipedia.org/wiki/ISO_639-3) code.

Note: The language files are NOT automatically downloaded.  If you do not have them installed via alternate means you can download them from https://github.com/tesseract-ocr/tessdata_best.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+spa")
true

julia> instance = TessInst()
Allocated Tesseract instance.

julia> tess_init(instance, "spa")
true
```

See also: [`TessInst()`](@ref)
