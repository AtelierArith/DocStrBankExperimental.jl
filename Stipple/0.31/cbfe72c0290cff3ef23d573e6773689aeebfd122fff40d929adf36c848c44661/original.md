```
add_click_info()
```

Adds information about the click event to the event object.

### Example

```julia @app begin     @in x = 1 end

@methods add*click*info

@event :myclick begin     @info event     notify(**model**, "(x, y) clicked: (:(event["clientX"]), :(event["clientY"]))") end

ui() = cell("Hello world!", @on(:click, :myclick, :addClickInfo))
