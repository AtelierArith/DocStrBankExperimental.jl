```
pix_write_pdf(
    stream::IO,
    pix::Pix;
    ppi::Integer = Int32(300),
    title::AbstractString = ""
)::Bool
```

Write an image to an IO stream as a PDF.  If there is an error `false` is returned.

**Arguments:**

| T   | Name   | Default      | Description                                            |
|:--- |:------ |:------------ |:------------------------------------------------------ |
| R   | stream |              | The stream to write the PDF to.                        |
| R   | pix    |              | The image to write to the PDF.                         |
| O   | ppi    | `Int32(300)` | The resolution of the image to use in pixels per inch. |
| O   | title  |              | The title to use in the PDF.                           |

**Restrictions:**

  * `ppi` - Must be greater than 0.
  * `title` - An empty string will result in no title being used in the PDF.

**Details:**

If the file exists it will be overwritten.  By default no title is added.
