  * `load(filename)` loads the contents of a formatted file, trying to infer the format from `filename` and/or magic bytes in the file (see [`query`](@ref)).
  * `load(strm)` loads from an `IOStream` or similar object. In this case, there is no filename extension, so we rely on the magic bytes for format identification.
  * `load(File{format"PNG"}(filename))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `load(Stream{format"PNG"}(io))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `load(f; options...)` passes keyword arguments on to the loader.
