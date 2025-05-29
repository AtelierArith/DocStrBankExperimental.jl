```
gmtfig(name::String; fmt=nothing, opts="")
```

Set attributes for the current modern mode session figure.

  * 'name' name of the new (or resumed) figure. It may contain an extension.
  * 'fmt'  figures graphics format (or formats, e.g. fmt="eps,pdf"). Not needed if 'name' has extension
  * 'opts' Sets one or more comma-separated options (and possibly arguments) that can be passed to psconvert when preparing this figure.
