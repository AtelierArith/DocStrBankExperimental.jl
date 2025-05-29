```julia
build(c::AbstractConnection, ...) -> ::AbstractComponent
```

The `build` function is used as the translation layer between the     `Olive` back-end and front-end. The client is HTML, these functions build      an HTML representation of a given parametric type. New cells, directories,      and projects can easily be created by extending this function with new methods.

```julia
# extensible methods for build:

build(c::Connection, om::OliveModifier, oe::OliveExtension{<:Any}) # load extensions

build(c::Connection, env::Environment{<:Any}) # environment extensions

build(c::Connection, dir::Directory{<:Any}) # directory extensions

build(c::AbstractConnection, cm::ComponentModifier, p::Project{<:Any}) # project extensions

build(c::Connection, cell::Cell{:dir}, d::Directory{<:Any}; bind::Bool = true) # file cells

build(c::Connection, cm::ComponentModifier, cell::Cell{<:Any}, proj::Project{<:Any}) # code cells
```

For example, the `:code` cell is added to `Olive` using the `Method`  `build(::Connection, ::ComponentModifier, ::Cell{:code}, ::Project{<:Any})`.

  * See also: `start`, `on_code_build`, `cell_highlight!`, `cell_bind!`, `evaluate`, `Cell`, `Project`
