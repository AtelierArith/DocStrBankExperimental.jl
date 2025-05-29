```
urldownload(url, progress = false;
            parser = nothing, format = nothing, save_raw = nothing,
            compress = :auto, multifiles = false, headers = HTTP.Header[],
            httpkw = Pair[], update_period = 1, kw...)
```

Download file from the corresponding `url` in memory and process it to the necessary data structure.

# Arguments

  * `url`: url of download
  * `progress`: show `ProgressMeter`, by default it is not shown
  * `parser`: custom parser, function that should accept one positional argument of the type `Vector{UInt8}` and optional keyword arguments and return necessary data structure. If parser is set than it overrides all other settings, such as `format`. If parser is not set, than internal parsers are used for data process.
  * `format`: one of the fixed formats (:CSV, :PIC, :FEATHER, :JSON), if set overrides autodetection mechanism.
  * `save_raw`: if set to `String` or `IO` then downloaded raw data is stored in corresponding stream.
  * `compress`: :auto by default, can be one of :none, :xz, :gzip, :bzip2, :lz4, :zstd, :zip. Determines whether file is compressed and compression type. Decompressed data is processed either by custom `parser` or by internal parser. By default for any compression type except of `:zip` internal parser is `CSV.File`, for `:zip` usual rules applies. If `compress` is `:none` than custom parser should decompress data on its own.
  * `multifiles`: `false` by default, for `:zip` compressed data defines, whether process only first file inside archive or return an array of decompressed and processed objects.
  * `headers`: `HTTP.jl` arguments that set http header of the request.
  * `httpkw`: `HTTP.jl` additional keyword arguments that is passed to the `GET` function. Should be supplied as a vector of pairs.
  * `update_period`: period of `ProgressMeter` update, by default 1 sec
  * `kw...`: any keyword arguments that should be passed to the data parser.
