```
print_html([io::IO,] parent_node::AbstractAnnotatedNode)

print_html([io::IO,] rag::AbstractRAGResult; add_sources::Bool = false,
	add_scores::Bool = false, default_styler = HTMLStyler(),
	low_styler = HTMLStyler(styles = "color:magenta", classes = ""),
	medium_styler = HTMLStyler(styles = "color:blue", classes = ""),
	high_styler = HTMLStyler(styles = "", classes = ""), styler_kwargs...)
```

Pretty-prints the annotation `parent_node` (or `RAGResult`) to the `io` stream (or returns the string) in HTML format (assumes node is styled with styler `HTMLStyler`).

It wraps each "token" into a span with requested styling (HTMLStyler's properties `classes` and `styles`). It also replaces new lines with `<br>` for better HTML formatting.

For any non-HTML styler, it prints the content as plain text.

# Returns

  * `nothing` if `io` is provided
  * or the string with HTML-formatted text (if `io` is not provided, we print the result out)

See also `HTMLStyler`, `annotate_support`, and `set_node_style!` for how the styling is applied and what the arguments mean.

# Examples

Note: `RT` is an alias for `RAGTools`

Simple start directly with the `RAGResult`:

```julia
# set up the text/RAGResult
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test answer. It has multiple sentences."
rag = RT.RAGResult(; context, final_answer=answer, question="")

# print the HTML
print_html(rag)
```

Low-level control by creating our `AnnotatedNode`:

```julia
# prepare your HTML styling
styler_kwargs = (;
	default_styler=RT.HTMLStyler(),
	low_styler=RT.HTMLStyler(styles="color:magenta", classes=""),
	medium_styler=RT.HTMLStyler(styles="color:blue", classes=""),
	high_styler=RT.HTMLStyler(styles="", classes=""))

# annotate the text
context = [
	"This is a test context.", "Another context sentence.", "Final piece of context."]
answer = "This is a test answer. It has multiple sentences."

parent_node = RT.annotate_support(
	RT.TrigramAnnotater(), answer, context; add_sources=false, add_scores=false, styler_kwargs...)

# print the HTML
print_html(parent_node)

# or to accumulate more nodes
io = IOBuffer()
print_html(io, parent_node)
```
