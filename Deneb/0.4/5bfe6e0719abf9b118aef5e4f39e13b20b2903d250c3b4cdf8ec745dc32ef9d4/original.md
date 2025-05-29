```
select_legend(name; encodings=:color, fields=nothing, bind_options=nothing)
```

Creates a `ParamSpec` named `name` that can be composed to other specs to create selectable legends bound to the given `encoding` or `field`. To customize the events that trigger legend interaction, set `bind_options` with a property that maps to a Vega event stream (e.g. "dblclick"). More info about legend binding: https://vega.github.io/vega-lite/docs/bind.html#legend-binding
