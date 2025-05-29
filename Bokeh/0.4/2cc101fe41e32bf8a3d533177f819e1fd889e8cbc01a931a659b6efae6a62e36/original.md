```
js_on_change(model, event, callbacks...)
```

Attach [`CustomJS`](@ref) callbacks to an arbitrary BokehJS model change event.

Change events for model properties are of the form `"change:property_name"` but as a convenience you can simply provide `"property_name"`.
