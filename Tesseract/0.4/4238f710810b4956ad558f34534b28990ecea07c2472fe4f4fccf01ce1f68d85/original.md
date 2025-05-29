```
pix_read_gif(
    filename::AbstractString
)::Union{Pix, Nothing}
```

Read a GIF image from the specified file.  Returns `nothing` on error.

**Arguments:**

|   T | Name     | Default |                       Description |
| ---:|:-------- | -------:| ---------------------------------:|
|   R | filename |         | The name of the GIF file to load. |
