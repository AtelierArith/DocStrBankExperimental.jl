```
PageNode(input; visible, collapsed)
PageNode(this_page, children; visible, collapsed)
```

Creates a `PageNode` object, which may have some children.

`input` can be anything that `pages` accepts in `Documenter.makedocs`, for example a string, a pair of strings, a vector of strings or pairs, or any combination thereof.

You can also specify details for the toplevel page and its children separately in the two-argument constructor.

## Examples

```julia
PageNode("index.md")
```

```julia
PageNode("Home" => "index.md")
```

```julia
PageNode(["index.md", "gallery.md"])
```
