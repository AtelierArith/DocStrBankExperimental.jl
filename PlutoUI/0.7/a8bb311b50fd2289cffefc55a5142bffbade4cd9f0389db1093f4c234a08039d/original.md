```
Resource(src::String, mime=mime_from_filename(src)[, html_attributes::Pair...])
```

A container for a URL-addressed resource that displays correctly in rich IDEs.

# Examples

```
Resource("https://julialang.org/assets/infra/logo.svg")
```

```
Resource("https://interactive-examples.mdn.mozilla.net/media/examples/flower.webm", :width => 100)
```

```
md"""
This is what a duck sounds like: $(Resource("https://interactive-examples.mdn.mozilla.net/media/examples/t-rex-roar.mp3"))
md"""
```
