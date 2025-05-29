**Base64 Interface**

### update_base64!(cm::ComponentModifier, name::String, raw::Any, filetype::String = "png") -> ::Component

---

Updates a given img component by name with the raw source as Base64

#### example

```julia
function serveb64(c::Connection)
      # this content could be a Julia Image, or a plot, in this example we assume
      #    julia_img is a PNG Julia image.
      image = base64img("myimage", julia_img, "png")
      on(c, image, "click") do cm::ComponentModifier
            update_base64!(cm, "image", other_julia_img, "png")
      end
      write!(c, image)
end
```
