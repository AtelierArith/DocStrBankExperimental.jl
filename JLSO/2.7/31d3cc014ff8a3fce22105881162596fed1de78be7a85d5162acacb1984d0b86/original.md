```
JLSOFile(data; format=:julia_serialize, compression=:gzip, kwargs...)
```

Stores the information needed to write a .jlso file.

# Arguments

  * `data` - The objects to be stored in the file.

# Keywords

  * `image=""` - The docker image URI that was used to generate the file
  * `julia=1.11.5` - The julia version used to write the file
  * `version=v"4"` - The file schema version
  * `format=:julia_serialize` - The format to use for serializing individual objects. While `:bson` is   recommended for longer term object storage, `:julia_serialize` tends to be the faster choice   for adhoc serialization.
  * `compression=:gzip`, what form of compression to apply to the objects.   Use `:none`, to not compress. `:gzip_fastest` for the fastest gzip compression,   `:gzip_smallest` for the most compact (but slowest), or `:gzip` for a generally good compromise.   Due to the time taken for disk IO, `:none` is not normally as fast as using some compression.
