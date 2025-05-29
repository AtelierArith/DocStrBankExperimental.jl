```
plot!(plot, item; ...)
plot!(plot, type; ...)
```

Adds a new item to the plot, or an item of the given type.

When passing a type, the allowed keyword arguments include anything accepted by the type. Some additional arguments are allowed depending on what `item` or `type` is.

The constructed item is returned. In the case of glyphs, the corresponding [`GlyphRenderer`](@ref) is returned instead.

## Glyphs

Additional keyword arguments:

  * Anything accepted by [`GlyphRenderer`](@ref).
  * `source`: Alias for `data_source`. May be a [`DataSource`](@ref), `Dict` of columns, or a `Tables.jl`-style table.
  * `color`: Alias for all the `*_color` properties.
  * `alpha`: Alias for all the `*_alpha` properties.
  * `palette`: If the glyph has a `color_mapper` property, it is set to a [`LinearColorMapper`](@ref) with this palette.
  * `legend_label`
  * `legend_field`
  * `legend_group`
  * `filters`: List of filters to apply to the source data.

## Renderers

This includes axes, grids, legends and other annotations.

Additional keyword arguments:

  * `location`: One of `"center"` (default), `"left"`, `"right"`, `"below"` or `"above"`.
  * `dimension`: For axes, you must specify either the `location` or `dimension` and the other one is inferred.

## Tools

Additional keyword arguments:

  * `activate`: If true, then set the tool as the active one of its kind on the toolbar.
