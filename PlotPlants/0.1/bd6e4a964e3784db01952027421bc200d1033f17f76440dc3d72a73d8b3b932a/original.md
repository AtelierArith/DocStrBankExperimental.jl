```
preview_dataset!(ax::PyObject, filename::String, label)
preview_dataset!(
            ax::PyObject,
            filename::String,
            label::String,
            format::FormatNC
)
```

Preview dataset, given

  * `filename` Dataset file to preview
  * `label` Label of the data to preview, variable name in NC files, band name in   TIFF files
  * `format` [`AbstractFormat`](@ref) type file format
