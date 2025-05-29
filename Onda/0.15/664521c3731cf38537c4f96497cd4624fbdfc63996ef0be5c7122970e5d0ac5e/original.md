```
load(signal[, span_relative_to_loaded_samples]; encoded::Bool=false)
load(file_path, file_format::Union{AbstractString,AbstractLPCMFormat},
     info[, span_relative_to_loaded_samples]; encoded::Bool=false)
```

Return the `Samples` object described by `signal`/`file_path`/`file_format`/`info`.

If `span_relative_to_loaded_samples` is present, return `load(...)[:, span_relative_to_loaded_samples]`, but attempt to avoid reading unreturned intermediate sample data. Note that the effectiveness of this optimized method versus the naive approach depends on the types of `file_path` (i.e. if there is a fast method defined for `Onda.read_byte_range(::typeof(file_path), ...)`) and `file_format` (i.e. does the corresponding format support random or chunked access).

If `encoded` is `true`, do not decode the `Samples` object before returning it.
