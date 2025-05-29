```
pix_read_spix(
    filename::AbstractString
)::Union{Pix, Nothing}
```

Read a SPIX image from the specified file.  Returns `nothing` on error.

**Arguments:**

| T   | Name     | Default | Description                        |
|:--- |:-------- |:------- |:---------------------------------- |
| R   | filename |         | The name of the SPIX file to load. |
