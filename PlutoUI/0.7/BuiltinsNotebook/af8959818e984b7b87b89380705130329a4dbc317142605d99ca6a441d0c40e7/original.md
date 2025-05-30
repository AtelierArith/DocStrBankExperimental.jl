A time input (`<input type="time">`) - the user can pick a time, the time is returned as `String` via `@bind` (e.g. `"15:45"`). Value is `""` until a time is picked.

Use `default` to set the initial value.

See the [Mozilla docs about `<input type="time">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/time)

# Examples

`@bind lunch_time TimeField()`

`@bind lunch_time TimeField(default=now())`
