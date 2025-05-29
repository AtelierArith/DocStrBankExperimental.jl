```
pix_read_spix(
    stream::IO
)::Union{Pix, Nothing}
```

Read a SPIX image from the specified stream.  Returns `nothing` on error.

**Arguments:**

| T   | Name   | Default | Description                               |
|:--- |:------ |:------- |:----------------------------------------- |
| R   | stream |         | The IO stream to read the SPIX file from. |

**Details:**

This implementation mirrors the API provided by Leptonica when you pass in a FILE pointer. This assumes that the remainder of the stream contains a SPIX image.
