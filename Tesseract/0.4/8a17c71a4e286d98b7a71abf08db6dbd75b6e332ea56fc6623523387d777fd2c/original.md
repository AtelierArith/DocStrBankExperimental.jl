```
pix_write_ps(
    pix::Pix;
    box::Union{PixBox, Nothing} = nothing,
    ppi::Integer = Int32(300),
    scale::AbstractFloat = Float32(1.0)
)::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array.  Returns 'nothing' if there was an error.

**Arguments:**

| T   | Name  | Default        | Description                                    |
|:--- |:----- |:-------------- |:---------------------------------------------- |
| R   | pix   |                | The image to write to a byte array.            |
| O   | box   | `nothing`      | Location to have the image appear on the page. |
| O   | ppi   | `Int32(300)`   | The resolution to use for the image.           |
| O   | scale | `Float32(1.0)` | Scale the image on the page.                   |

**Restrictions:**

  * `ppi` - Must be greater than 0.
  * `scale` - Must be greater than or equal to `0.0`.

**Details:**

If you don't want the image scaled set the `scale` to `1.0`.  If you want to position the image on the page you can use a `box` however set `w` and `h` to `0`, then the image will be positioned where you want it and not scaled.

If you want the image to be a specific size set the scale to `0.0` and use a box setting `w` and `h` to the width and height you want in thousandth of an inch.  So a width of `5000` and a height of `2000` will give you an image that is 5 inches across and 2 inches high.

If you want the image scaled set the `scale` to the factor you desire.  Value of `0.5` will cause the image to be halfed, while a value of `2.0` will double the size of the image.  If you want to also position the image on the page use a `box` but set the `w` and `h` values to `0`.
