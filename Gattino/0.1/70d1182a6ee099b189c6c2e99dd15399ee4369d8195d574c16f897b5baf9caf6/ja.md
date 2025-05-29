##### コンテキスト

```julia
context -> ::AbstractContext
```

`Context`は、SVGウィンドウにスケーリングされた形状を描画するために使用できる`Component{:svg}`のラッパーです。コンテキストは通常、この関数のメソッドを通じて作成され、通常は`Function`と`context`の寸法を取ります。

`Context`のスケーリングを`Context`から調整するには、`group`を使用します。

  * `group`

Gattinoのミューテーションメソッド（`Gattino._`）は、コンテキストコンポーネントやコンテキストプロッティングから使用できます（`?Gattino.context_components`、`?Gattino.context_plotting`）、または`Vector{Servable}`から`draw!`を使用して`Toolips`コンポーネントを描画できます。

  * `draw!`
  * `Gattino.context_components`
  * `Gattino.context_plotting`

####### レイヤー コンテキストにはレイヤーがあり、`Toolips`構文の混合を使用してミューテートできます。例えば、`style!`や`Gattino`レイヤー編集関数などです。これには以下が含まれます...

  * `open_layer!`
  * `delete_layer!`
  * `rename_layer!`
  * `move_layer!`
  * `reshape(con::AbstractContext, layer::String, into::Symbol; args ...)`
  * `style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)`
  * `style!(con::AbstractContext, spairs::Pair{String, String} ...)`
  * `animate!(con::AbstractContext, layer::String, anim::ToolipsSVG.ToolipsServables.Animation)`

新しいレイヤーはグルーピングを使用して作成できます。

  * `group!`

####### メソッド
