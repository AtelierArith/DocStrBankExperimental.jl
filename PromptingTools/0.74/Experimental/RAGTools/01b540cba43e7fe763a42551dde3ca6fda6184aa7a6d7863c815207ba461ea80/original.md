```
PromptingTools.pprint(
    io::IO, node::AbstractAnnotatedNode;
    text_width::Int = displaysize(io)[2], add_newline::Bool = true)
```

Pretty print the `node` to the `io` stream, including all its children

Supports only `node.style::Styler` for now.
