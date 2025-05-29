```
pix_write_gif(
    stream::IO,
    pix::Pix
)::Bool
```

Write an image to an IO stream in the GIF image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name   | Default | Description                       |
|:--- |:------ |:------- |:--------------------------------- |
| R   | stream |         | The IO stream to write to.        |
| R   | pix    |         | The image to write to the stream. |
