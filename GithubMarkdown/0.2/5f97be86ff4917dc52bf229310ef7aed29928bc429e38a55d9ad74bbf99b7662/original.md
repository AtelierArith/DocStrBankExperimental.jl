```
rendergfm(output::IO, input::IO; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
rendergfm(output::IO, input::AbstractString; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
rendergfm(output::AbstractString, input::AbstractString; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
```

Render the markdown document `input` to `output`, following the cmark-gfm spec.

  * `documenter`: Wraps the output in a Documenter `@raw`-block of the specified format.
  * `format`: Can be one of `html`, `xml`, `man`, `commonmark`, `plaintext`, `latex`.
  * `removehtml`: Removes all literal HTML input and potentially dangerous links if `true`. `false` by default. The `tagfilter` extension (enabled by default) will remove most malicious raw HTML. It's recommended to sanitize the resulting HTML when `removehtml == false`.
  * `extensions`: An array of extensions to use. Valid extensions are `footnotes`, `table`, `strikethrough`, `autolink`, `tagfilter`, `tasklist`. All of those are enabled by default.

Spec: https://github.github.com/gfm/
