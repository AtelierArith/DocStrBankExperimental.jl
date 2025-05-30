A color input (`<input type="color">`) - the user can pick an RGB color, the color is returned as color hex `String` via `@bind`. The value is lowercase and starts with `#`.

Use `default` to set the initial value.

See the [Mozilla docs about `<input type="color">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color)

# Examples

`@bind color ColorStringPicker()`

`@bind color ColorStringPicker(default="#aabbcc")`
