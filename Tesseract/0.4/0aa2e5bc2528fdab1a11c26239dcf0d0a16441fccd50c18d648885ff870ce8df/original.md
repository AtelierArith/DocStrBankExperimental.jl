```
pix_read_pnm(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a PNM image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | data |         | The byte array to read the PNM image from. |
