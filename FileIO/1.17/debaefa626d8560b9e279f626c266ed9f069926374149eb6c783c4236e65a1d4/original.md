Some packages may implement a streaming API, where the contents of the file can be read in chunks and processed, rather than all at once. Reading from these higher-level streams should return a formatted object, like an image or chunk of video or audio.

  * `loadstreaming(filename)` loads the contents of a formatted file, trying to infer the format from `filename` and/or magic bytes in the file. It returns a streaming type that can be read from in chunks, rather than loading the whole contents all at once.
  * `loadstreaming(strm)` loads the stream from an `IOStream` or similar object. In this case, there is no filename extension, so we rely on the magic bytes for format identification.
  * `loadstreaming(File{format"WAV"}(filename))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `loadstreaming(Stream{format"WAV"}(io))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `loadstreaming(f; options...)` passes keyword arguments on to the loader.
