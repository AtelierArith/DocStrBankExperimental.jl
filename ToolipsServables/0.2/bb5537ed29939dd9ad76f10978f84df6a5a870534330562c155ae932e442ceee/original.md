```julia
abstract type AbstractComponent <: Servable
```

Components are html elements or CSS classes. 

  * `name`**::String**
  * `string`**::AbstractComponent**
  * `properties`**::Dict{Symbol, <:Any}**
  * See also: `Component`, `Servable`, `StyleComponent`, `style!`

```
