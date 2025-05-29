```
HTMLPrinter(buf::IO; root_class="", root_tag="pre", callback=nothing)
```

Creates a printer for `MIME"text/html"` output.

# Arguments

  * `buf`: A source `IO` object containing a text with ANSI escape codes.
  * `root_class`: The `class` attribute value for the root element.
  * `root_tag`: The tag name for the root element.
  * `callback`: A callback method (see below).

# Callback method

```
callback(io::IO, printer::HTMLPrinter, tag::String, attrs::Dict{Symbol, String})
```

The `callback` method will be called just before writing HTML tags.

## Callback arguments

  * `io`: The destination `IO` object.
  * `printer`: The `HTMLPrinter` in use.
  * `tag`: The HTML tag to be written. For closing tags, they have the prefix "/".
  * `attrs`: A dictionary consisting of pairs of a `Symbol` for the attributes (e.g. `:class`, `:style`) and the `String` for its value.

## Callback return value

If the return value is `nothing`, the printer writes the HTML tag to the `io` according to the `tag` and the `attrs` after the call. If the return value is not `nothing`, this default writing will be prevented.
