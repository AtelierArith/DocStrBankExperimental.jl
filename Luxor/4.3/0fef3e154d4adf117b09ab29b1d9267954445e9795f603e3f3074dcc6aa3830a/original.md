```
textformat(e1, e2, e3...;
    color=getcolor(),
    fontsize=get_fontsize(),
    fontface="Helvetica",
    leading=120,
    baseline=0,
    prolog=nothing,
    advance=1.0,
    position=Point(0, 0),
    width=300)
```

Draw the text in elements `e1`, `e2`, ... Each element can be either:

  * a string
  * a named tuple containing text and formatting parameters:

Text starts at `position` and is constrained by the `width`.

A named tuple element can be something like this:

```julia
(
    text= "a string",
    color = "blue",
    fontsize = 12,
    fontface = "JuliaMono-Italic",
    leading = 100,
    baseline = 0,
    advance = 1.0,
    prolog = nothing
)
```

If `advance` is 1.0, elements are separated by a space; otherwise by `advance` units (positive shifts to the right).

`baseline` is usually 0, but positive values move the text upwards.

`leading` here is a percentage, relative to the font size; the default is 120%.

`prolog` calls a function with arguments `(position::Point, str::String)`, which is called before the text is drawn.

Returns the point where the next text would be placed.

This function uses the Toy text API.

## Example

This example draws a bold heading in red, and a paragraph below in monospaced text, in orange.

```julia
@draw begin
    background("black")
    fontsize(20)
    textformat(
        (text="Heading",
            fontface="AvenirNext-Heavy",
            fontsize=40,
            leading=100,
            color = "red",
        ),
        (text="The first paragraph.",
            fontface = "JuliaMono-Light",
            fontsize = 20,
            color="orange"
        ),
    position = boxtopleft() + (100, 100),
    width = 150
    )
end
```
