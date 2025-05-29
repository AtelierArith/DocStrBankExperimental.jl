```
pix_write_pam(
    stream::IO,
    pix::Pix
)::Bool
```

Write an image to an IO stream in the PAM image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name   | Default | Description                          |
|:--- |:------ |:------- |:------------------------------------ |
| R   | stream |         | The IO stream to write the image to. |
| R   | pix    |         | The image to write to the stream.    |
