```
pix_write_spix(
    filename::AbstractString,
    pix::Pix
)::Bool
```

Write an image to a file in the SPIX image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name     | Default | Description                       |
|:--- |:-------- |:------- |:--------------------------------- |
| R   | filename |         | The name of the file to write to. |
| R   | pix      |         | The image to write to the file.   |

**Details:**

If the file exists it will be overwritten.
