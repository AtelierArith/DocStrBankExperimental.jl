```
read_frames(file[, range])
```

Read a sequence of frames from the ExtXYZ `file`, which can be specified by a file pointer, filename, IOStream or IOBuffer.

`range` can be a single integer, range object or integer array of frame indices.

Reading from IOBuffers is currently not supported on Windows.
