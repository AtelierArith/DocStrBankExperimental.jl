```
Show(mime::MIME, data)
```

An object that can be rendered as the `mime` MIME type, by writing `data` to the IO stream. For use in environments with rich output support. Read more about [`Base.show`](@ref).

# Examples

```julia
Show(MIME"text/html"(), "I can be <b>rendered</b> as <em>HTML</em>!")
```

```julia
Show(MIME"image/png"(), read("dog.png"))
```

`Base.showable` and `Base.show` are defined for a `Show`.

```julia
s = Show(MIME"text/latex"(), "\\frac{hello}{world}")

showable(MIME"text/latex"(), s) == true

repr(MIME"text/latex"(), s) == "\\frac{hello}{world}"
```
