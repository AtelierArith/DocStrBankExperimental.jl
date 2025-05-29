```
upload_all_to_gist!(
    artifacts_toml::AbstractString;
    extension::AbstractString = ".tar.gz",
    private::Bool = true,
    append::Bool = false,
)
```

Upload all artifact entries in `artifacts_toml` without the `.download.url` property (by default) and then update `artifacts_toml`.

# Keyword Arguments

  * `extension`: file extension for of artifact archive files
  * `private`: if `true`, upload the archives to a private gist
  * `append`: if `true`, upload the archives even if the `download` entries exist
