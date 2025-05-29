```
update_languages(
    languages::AbstractString = "eng";
    target::AbstractString = "tessdata",
    frequency::Integer = 7,
    source::GitHubProject = DATA_REPO
)::Bool
```

Update the training data files for the specified languages.  Returns false if there was an error updating the files.

**Arguments:**

| T   | Name      | Default    | Description                                            |
|:--- |:--------- |:---------- |:------------------------------------------------------ |
| O   | languages | `eng`      | The languages to update separated with "+".            |
| K   | target    | `tessdata` | The directory to save the data files in.               |
| K   | frequency | `7`        | How often to check for updates on the server in days.  |
| K   | source    | ...        | The GitHub project to download the training data from. |

**Details:**

By default the data files are saved in a "tessdata" directory under the current directory. The training data is normally downloaded from the https://github.com/tesseract-ocr/tessdata_best GitHub project.

See also: [`download_languages`](@ref)
