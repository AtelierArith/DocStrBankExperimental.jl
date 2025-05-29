```
pix_write_pdf(
    pix::Pix;
    ppi::Integer = Int32(300),
    title::AbstractString = ""
)::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array as a PDF.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name  | Default      | Description                                            |
|:--- |:----- |:------------ |:------------------------------------------------------ |
| R   | pix   |              | The image to write to the PDF.                         |
| O   | ppi   | `Int32(300)` | The resolution of the image to use in pixels per inch. |
| O   | title |              | The title to use in the PDF.                           |

**Restrictions:**

  * `ppi` - Must be greater than 0.
  * `title` - An empty string will result in no title being used in the PDF.

**Details:**

By default no title is added.
