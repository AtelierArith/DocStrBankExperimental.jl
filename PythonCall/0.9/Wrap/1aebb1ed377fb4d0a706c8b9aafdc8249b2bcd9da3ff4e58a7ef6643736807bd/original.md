```
PyIO(x; own=false, text=missing, line_buffering=false, buflen=4096)
```

Wrap the Python IO stream `x` as a Julia IO stream.

When this goes out of scope and is finalized, it is automatically flushed. If `own=true` then it is also closed.

If `text=false` then `x` must be a binary stream and arbitrary binary I/O is possible. If `text=true` then `x` must be a text stream and only UTF-8 must be written (i.e. use `print` not `write`). If `text` is not specified then it is chosen automatically. If `x` is a text stream and you really need a binary stream, then often `PyIO(x.buffer)` will work.

If `line_buffering=true` then output is flushed at each line.

For efficiency, reads and writes are buffered before being sent to `x`. The size of the buffers is `buflen`. The buffers are cleared using `flush`.
