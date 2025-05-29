```julia
build(c::Connection, cm::ComponentModifier, cell::Cell{<:Any},
proj::Project{<:Any}) -> ::Component{:div}
```

The catchall/default `build` function for session cells. This function is what creates the gray boxes for cells that Olive cannot create. Using this function as a template, you can create your own olive cells.

```

```

Also important for cells:

  * `cell_bind!`
  * `build_base_cell`
  * `evaluate`
  * `ToolipsSession.bind`
  * `cell_highlight!`
  * `olive_save`
  * `string`

And code cells can be extended with

  * `on_code_evaluate`
  * `on_code_highlight`
  * `on_code_build`
