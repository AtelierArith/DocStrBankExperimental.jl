```
pix_get_dimensions(
    pix::Pix
)::Union{NamedTuple{(:w, :h, :d), Tuple{Int32, Int32, Int32}}, Nothing}
```

Retrieve the dimensions of the image.

**Arguments:**

|   T | Name | Default | Description                         |
| ---:|:---- |:------- |:----------------------------------- |
|   R | pix  |         | The image to get the dimensions of. |

**Details:**

This method returns a named tuple:

  * w - Image width.
  * h - Image height.
  * d - Color depth.

See also: [`pix_get_depth`](@ref)
