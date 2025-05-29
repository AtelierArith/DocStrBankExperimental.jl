Some packages may implement a streaming API, where the contents of the file can be written in chunks, rather than all at once. These higher-level streams should accept formatted objects, like an image or chunk of video or audio.

  * `savestreaming(filename, data...)` saves the contents of a formatted file, trying to infer the format from `filename`.
  * `savestreaming(File{format"WAV"}(filename))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `savestreaming(Stream{format"WAV"}(io))` specifies the format directly, and bypasses the format [`query`](@ref).
  * `savestreaming(f, data...; options...)` passes keyword arguments on to the saver.
