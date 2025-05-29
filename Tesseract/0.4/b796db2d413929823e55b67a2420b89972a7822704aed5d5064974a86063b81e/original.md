```
tess_read_debug_config(
    inst::TessInst,
    filename::AbstractString
)::Nothing
```

Load debug configuration settings from a file into the Tesseract instance.

**Arguments:**

| T   | Name     | Default | Description                                       |
|:--- |:-------- |:------- |:------------------------------------------------- |
| R   | inst     |         | The Tesseract instance to load the settings into. |
| R   | filename |         | The name of the file to load the settings from.   |

**Details:**

Only the debug settings will be loaded, all other settings will be ignored.

See also: [`tess_read_config`](@ref)
