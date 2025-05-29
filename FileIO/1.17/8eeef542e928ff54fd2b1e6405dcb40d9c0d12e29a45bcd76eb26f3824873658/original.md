  * `save(filename, data...)` saves the contents of a formatted file, trying to infer the format from `filename`.
  * `save(Stream{format"PNG"}(io), data...)` specifies the format directly, and bypasses the format [`query`](@ref).
  * `save(File{format"PNG"}(filename), data...)` specifies the format directly, and bypasses the format [`query`](@ref).
  * `save(f, data...; options...)` passes keyword arguments on to the saver.
