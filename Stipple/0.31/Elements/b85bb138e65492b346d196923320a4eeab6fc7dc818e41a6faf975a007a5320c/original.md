```
on(action, expr)
```

Defines a js routine that is called by the given `action` of the Vue component, e.g. `:click`, `:input`

### Example

```julia
julia> input("", @bind(:input), @on("keyup.enter", "process = true"))
"<input  v-model='input' v-on:keyup.enter='process = true' />"
```

If `expr` is a symbol, the event will be sent to the backend. In order to handle the event a respective `Stipple.notify` method needs to be defined either manually or via the `@event` macro.

### Example

```julia
julia> Stipple.notify(model, ::Val{:my_click}) = println("clicked")
```

or if event information is needed

```julia
Stipple.notify(model, ::Val{:my_click}, event_info) = println(event_info)
```

or via the `@event` macro:

```julia
@event :my_click begin
  @info "clicked, event_info is " event
  notify(__model__, "Info from the backend: Clicked")
end
```

Note that in the handler `model` refers to the receiving model and event is a Dict of event information. The handler is linked in the ui-element

```julia
btn("Event test", @on("click", :my_click))
```

Sometimes preprocessing of the events is necessary, e.g. to add or skip information

```julia
@on(:uploaded, :uploaded, "for (f in event.files) { event.files[f].fname = event.files[f].name }")
```

This is necessary because in some cases, e.g. in case of the click event not all fields are automatically converted by JSON.stringify. Other events, e.g. the `row-clicked` event of the `q-table` component pass more arguments than just the event itself. These arguments are accessible as `args`.

```julia
table(:table, @on(:row__click, :rowclick, "event.row = args[0]"))
```

You can also use predefined handlers as preprocessors. This is useful if you want to use the same handler for multiple events. Handler names are passed as Symbols.

```julia
@methods [
    :addTableIndex => js"""
        function (event, row, id) {
            const keys = Object.keys(row)
            event.row = id + 1;
            event.column = event.target.closest('td').cellIndex + 1;
            event.value = row[keys[event.column]];
            event.row_data = row;
            event.column_keys = keys;
            return event;
        }
    """
]

cell(@on(:click, :rowclick, :addTableIndex))
```

Finally, you can also pass arrays of handlers as preprocessors, make sure in this case that each handler returns the event object, as the handlers are chained. Mixing of symbols and strings is also possible.

```julia
cell(@click("rowclick", [:addTableIndex, "console.log('Click coords: ' + event.clientX + '|' + event.clientY)", :myHandler]))
```
