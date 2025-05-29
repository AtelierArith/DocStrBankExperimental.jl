```
set_close_to!(slider, value) -> closest_value
```

Set the `slider` to the value in the slider's range that is closest to `value` and return this value. This function should be used to set a slider to a value programmatically, rather than mutating its value observable directly, which doesn't update the slider visually.
