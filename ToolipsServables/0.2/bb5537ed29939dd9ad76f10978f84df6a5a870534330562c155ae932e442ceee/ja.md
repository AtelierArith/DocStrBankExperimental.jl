```julia
abstract type AbstractComponent <: Servable
```

コンポーネントはHTML要素またはCSSクラスです。

  * `name`**::String**
  * `string`**::AbstractComponent**
  * `properties`**::Dict{Symbol, <:Any}**
  * 参照: `Component`, `Servable`, `StyleComponent`, `style!`

```
