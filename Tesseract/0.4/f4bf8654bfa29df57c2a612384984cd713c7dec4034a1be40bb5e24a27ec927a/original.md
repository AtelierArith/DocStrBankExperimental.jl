```
pix_read_pnm(
    filename::AbstractString
)::Union{Pix, Nothing}
```

Read a PNG image from the specified file.  Returns `nothing` on error.

**Arguments:**

| T   | Name     | Default | Description                       |
|:--- |:-------- |:------- |:--------------------------------- |
| R   | filename |         | The name of the PNM file to load. |
