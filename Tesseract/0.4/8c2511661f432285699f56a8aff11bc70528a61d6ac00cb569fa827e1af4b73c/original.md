```
pix_write_pnm(
    pix::Pix
)::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array in the PNM image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name | Default | Description                         |
|:--- |:---- |:------- |:----------------------------------- |
| R   | pix  |         | The image to write to a byte array. |
