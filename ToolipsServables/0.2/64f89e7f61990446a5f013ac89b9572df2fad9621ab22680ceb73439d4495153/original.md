```julia
Component{T <: Any} <: AbstractComponent <: Servable
```

  * `name`**::String**
  * `properties`**::Dict{Symbol, Any}**
  * `tag`**::String**

The `Component` is the `ToolipsServables` structure for representing an `HTML` element. Components may be indexed using both strings and symbols; they are typed to their element name,  but the `tag` field will be the element tag written. Components may be composed with `push!` and  `set_children!`, styled with `style!`, and are written to a `Connection` with `write!`.

`Components` initialize with a few special properties (if they are not provided); `:text`, `:children`, and `:extras`.

  * :extras are written before the `Component`.
  * :children are written inside of the `Component`.
  * :text is also written inside of the `Component`.

Components are usually constructed through high-level constants, which are calls to the  `Component{T}(name::String = "-", properties ...; args ...)` constructor.

  * See also: `templating`, `StyleComponent`, `AbstractComponent`, `elements`, `arguments`

```julia
Component{T}(name::String, tag::String, properties::Dict{Symbol, Any}) where {T <: Any}
Component{T}(name::String = "-", properties ...; args ...) where {T <: Any}
Component(tag::String, name::String, props::Any ...; args ...)
```

```example
using ToolipsServables
# using Toolips.Components
# creating components
myd::Component{:div} = div("example", text = "hello world!")

myheading::Component{:h1} = h1("myheading", text = "example")

elements::Vector{<:AbstractComponent} = [p("example", text = e) for e in 1:10]

# composing components
style!(myheading, "color" => "white", "font-size" => 10pt)
push!(myd, myheading)
set_children!(myheading, elements)
# writing components
buff = IOBuffer()
write!(buff, myd)
str = ""
write!(str, myd)
using Toolips
c = Toolips.SpoofConnection()
write!(c, myd)
```
