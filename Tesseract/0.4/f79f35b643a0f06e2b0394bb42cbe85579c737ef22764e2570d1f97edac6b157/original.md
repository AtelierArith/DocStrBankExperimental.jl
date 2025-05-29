```
download_languages(
    languages::AbstractString = "eng";
    target::AbstractString = "tessdata",
    baseUrl::AbstractString = DATA_URL,
    force::Bool = false
)::Bool
```

Download the data files for the specified languages.  Returns `false` if there is a problem downloading the files.

**Arguments:**

| T   | Name      | Default    | Description                                        |
|:--- |:--------- |:---------- |:-------------------------------------------------- |
| O   | languages | `eng`      | The languages to download separated with "+".      |
| K   | target    | `tessdata` | The directory to save the data files in.           |
| K   | baseUrl   | ...        | The base URL to download the files from.           |
| K   | force     | `false`    | Should the files be downloaded even if they exist? |

**Details:**

By default the data files are saved in a "tessdata" directory under the current directory, and the files are downloaded from https://github.com/tesseract-ocr/tessdata_best.

Normally if the file has already been downloaded then it is not downloaded again.  However if `force` is true then the file is downloaded and the existing file is overwritten.

See also: [`update_languages`](@ref)
