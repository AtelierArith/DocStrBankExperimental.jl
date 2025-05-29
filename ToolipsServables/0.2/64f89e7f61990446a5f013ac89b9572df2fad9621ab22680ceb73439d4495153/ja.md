```julia
Component{T <: Any} <: AbstractComponent <: Servable
```

  * `name`**::String**
  * `properties`**::Dict{Symbol, Any}**
  * `tag`**::String**

`Component`は`HTML`要素を表すための`ToolipsServables`構造体です。コンポーネントは文字列とシンボルの両方を使用してインデックス付けでき、要素名に型付けされていますが、`tag`フィールドには書かれた要素タグが入ります。コンポーネントは`push!`や`set_children!`で構成され、`style!`でスタイルが適用され、`write!`で`Connection`に書き込まれます。

`Components`は、いくつかの特別なプロパティ（提供されていない場合）で初期化されます；`:text`、`:children`、および`:extras`。

  * :extrasは`Component`の前に書かれます。
  * :childrenは`Component`の内部に書かれます。
  * :textも`Component`の内部に書かれます。

コンポーネントは通常、高レベルの定数を通じて構築され、これは`Component{T}(name::String = "-", properties ...; args ...)`コンストラクタへの呼び出しです。

  * 参照: `templating`、`StyleComponent`、`AbstractComponent`、`elements`、`arguments`

```julia
Component{T}(name::String, tag::String, properties::Dict{Symbol, Any}) where {T <: Any}
Component{T}(name::String = "-", properties ...; args ...) where {T <: Any}
Component(tag::String, name::String, props::Any ...; args ...)
```

```example
using ToolipsServables
# using Toolips.Components
# コンポーネントの作成
myd::Component{:div} = div("example", text = "hello world!")

myheading::Component{:h1} = h1("myheading", text = "example")

elements::Vector{<:AbstractComponent} = [p("example", text = e) for e in 1:10]

# コンポーネントの構成
style!(myheading, "color" => "white", "font-size" => 10pt)
push!(myd, myheading)
set_children!(myheading, elements)
# コンポーネントの書き込み
buff = IOBuffer()
write!(buff, myd)
str = ""
write!(str, myd)
using Toolips
c = Toolips.SpoofConnection()
write!(c, myd)
```
