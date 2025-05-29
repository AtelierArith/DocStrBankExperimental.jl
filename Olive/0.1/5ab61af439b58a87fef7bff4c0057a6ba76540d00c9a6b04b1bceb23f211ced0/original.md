```julia
build(c::Connection, dir::Directory{<:Any}) -> ::Component{:div}
```

The `build` function for an `Olive.Directory`. This function could be extended to create new      direcotry types. `import` `Olive.build` and create a new `build(c::Connection, dir::Directory{:custom})`      binding to do so.
