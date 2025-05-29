```
pix_read(
    stream::IO
)::Union{Pix, Nothing}
```

Load an image from from a stream.  Returns `nothing` if the file could not be loaded.

**Arguments:**

| T   | Name   | Default | Description                        |
|:--- |:------ |:------- |:---------------------------------- |
| R   | stream |         | The stream to read the image from. |

**Details:**

This implementation mirrors the API provided by Leptonica when you pass in a FILE pointer. This assumes that the remainder of the stream contains an image, so the remainder of the stream will be read and decoded as an image.
