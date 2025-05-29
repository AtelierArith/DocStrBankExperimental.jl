```
pix_read_spix(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a SPIX image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                 |
|:--- |:---- |:------- |:------------------------------------------- |
| R   | data |         | The byte array to read the SPIX image from. |
