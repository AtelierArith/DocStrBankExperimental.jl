A color input (`<input type="color">`) - the user can pick an RGB color, the color is returned as color hex `String` via `@bind`. The value is lowercase and starts with `#`.

Use `default` to set the initial value.

# Examples

`@bind color ColorStringPicker()`

`@bind color ColorStringPicker(default="#aabbcc")`

# See also

[`ColorPicker`](@ref)
