```
PromptingTools.pprint(
	io::IO, node::AbstractAnnotatedNode;
	text_width::Int = displaysize(io)[2], add_newline::Bool = true)
```

`node`を`io`ストリームに整形して印刷し、そのすべての子を含めます。

現在のところ、`node.style::Styler`のみをサポートしています。
