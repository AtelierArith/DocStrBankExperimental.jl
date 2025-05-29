```
pix_read_bmp(
    filename::AbstractString
)::Union{Pix, Nothing}
```

Read a BMP image from the specified file.  Returns `nothing` on error.

**Arguments:**

| T   | Name     | Default | Description                       |
|:--- |:-------- |:------- |:--------------------------------- |
| R   | filename |         | The name of the BMP file to load. |
