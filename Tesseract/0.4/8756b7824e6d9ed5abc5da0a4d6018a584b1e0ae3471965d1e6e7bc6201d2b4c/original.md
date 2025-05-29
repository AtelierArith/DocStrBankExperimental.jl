```
pix_write_pam(
    pix::Pix
)::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array in the PAM image format.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name | Default | Description                           |
|:--- |:---- |:------- |:------------------------------------- |
| R   | pix  |         | The image to write to the byte array. |
