**Base64 Interface**

### base64img(name::String, raw::Any, filetype::String = "png") -> ::Component

---

Creates a Base64 image component from any type shown with the image/**filetype** mime. For example, a plot which only shows as a png.

#### example

```
function serveb64(c::Connection)
      # this content could be a Julia Image, or a plot, in this example we assume
      #    julia_img is a PNG Julia image.
      image = base64img(julia_img, "png")
      write!(c, image)
end
```
