```
update_theme!(with_theme::Theme; kwargs...)
```

Update the current theme incrementally. This means that only the keys given in `with_theme` or through keyword arguments are changed, the rest is left intact. Nested attributes are either also updated incrementally, or replaced if they are not attributes in the new theme.

# Example

To change the default colormap to `:greys`, you can pass that attribute as a keyword argument to `update_theme!` as demonstrated below.

```
update_theme!(colormap=:greys)
```

This can also be achieved by passing an object of types `Attributes` or `Theme` as the first and only positional argument:

```
update_theme!(Attributes(colormap=:greys))
update_theme!(Theme(colormap=:greys))
```
