**Toolips Markdown**

### tmd(name::String = "tmd", s::String = "") -> ::Component

---

Turns a markdown string into a Toolips Component. Markdown will always use default styling.

#### example

```
route("/") do c::Connection
    mymdcomp = tmd("mainmarkdown", "# Hello! [click](http://toolips.app/)")
    write!(c, mymdcomp)
end
```
