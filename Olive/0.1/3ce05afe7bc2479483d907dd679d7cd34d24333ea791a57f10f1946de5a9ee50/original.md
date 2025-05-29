```
build(c::Connection, cell::Cell{<:Any}, d::Directory{<:Any}) -> ::Component{:div}
```

The catchall/default `build` function for directory cells. This function is what creates the gray boxes for files that Olive cannot read inside of directories. Using this function as a template, you can create your own directory cells. Write a new method for this function in order to build cells for a new file type. Note that you might also want to extend `olive_save` in order to save your new file type. Bind `dblclick` and use the `load_session` or `add_to_session` methods, dependent on `explorer`... Which should also be `false` by default. `directory_cells` will put the file path into `cell.outputs` and the file name into `cell.source`.

```julia

```

Here are some other **important** functions to look at for creating file cells:

  * `build_base_cell`
  * `evaluate`
  * `olive_save`
  * `olive_read`
