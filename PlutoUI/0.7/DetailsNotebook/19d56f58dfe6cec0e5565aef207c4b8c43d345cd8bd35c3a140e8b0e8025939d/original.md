```julia
details(summary, contents; open::Bool=false)
```

Create a collapsable details disclosure element (`<details>`).

Useful for initially hiding content that may be important yet overly verbose or exposing advanced variables that may not always need displayed.

# Arguments

  * `summary::Any`: the always visible summary of the details element.
  * `contents::Any`: the item(s) to nest within the details element.

# Keyword arguments

  * `open::Bool=false`: whether the details element is initially open.

# Examples

```julia
details("My summary", "Some contents")
```

```julia
details(
	"My summary",
	[
		"My first item",
		(@bind my_var Slider(1:10)),
		md"How are you feeling? $(@bind feeling Slider(1:10))",
	],
	open=true,
)
```

!!! warning "Beware @bind in collection declaration"
    You may want to `@bind` several variables within the `contents` argument by declaring a collection of `@bind` expressions. **Wrap each `@bind` expression in parenthesis** or interpolate them in `md` strings like the example above to prevent macro expansion from modifying how your collection declaration is interpreted.


```julia
# This example will cause an error
details(
	"My summary",
	[
		"My first item",
		@bind my_var Slider(1:10),
	]
)
```
