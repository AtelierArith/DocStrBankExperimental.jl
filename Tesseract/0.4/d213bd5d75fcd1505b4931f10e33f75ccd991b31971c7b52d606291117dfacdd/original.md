```
TessInst(
    languages::AbstractString = "eng",
    dataPath::AbstractString = TESS_DATA
)
```

Construct an initialize a TessInst object.

**Arguments:**

| T   | Name      | Default    | Description                                      |
|:--- |:--------- |:---------- |:------------------------------------------------ |
| O   | languages | `eng`      | The language(s) to load.                         |
| O   | dataPath  | `tessdata` | The directory to look for the language files in. |

**Details:**

To change the langauges identified by this instance you can call `tess_init()`.  Multiple langagues can be specified by seperating them with a plus.  So if you want english and spanish you could specify "eng+spa".  The language codes are (usually) the [ISO 639-3](https://en.wikipedia.org/wiki/ISO_639-3) code.

**Example:**

```jldoctest
julia> using Tesseract

julia> download_languages("eng+fra")
true

julia> instance = TessInst("eng+fra")
Allocated Tesseract instance.
```

See also: [`tess_init`](@ref).
