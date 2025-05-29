```
slider(range::AbstractRange{<:Union{Symbol, String, Real}}, fieldname::Union{Symbol,Nothing} = nothing, args...; lazy = false, kwargs...)
```

## `slider`は、ユーザーが最小値と最大値の間で数値を指定するための優れた方法であり、有効な値の間にオプションのステップを持つことができます。スライダーにはフォーカスインジケーター（ハイライトされたスライダーボタン）もあり、これによりスライダーのキーボード調整が可能です。

### 例

---

### 表示

```julia-repl
julia> slider(1:5:100)
```

---

### 引数

---

1. 動作

      * `name::String` - コントロールの名前を指定するために使用されます; URLに直接送信されるフォームを扱う場合に便利です。例: `car_id`
      * `snap::Bool` - 自由にスライドするのではなく、有効な値にスナップします; 提案: 'step'プロパティと一緒に使用
      * `reverse::Bool` - 逆方向で動作します（方向を変更）
      * `vertical::Bool` - 垂直方向に表示します
      * `labelalways::Bool` - ラベルを常に表示します
2. コンテンツ

      * `label::Bool` - ユーザーがスライダーのサムをクリック/タップして移動するときにラベルをポップアップします
      * `markers::Union{Bool, Int}` - トラック上にマーカーを表示します。モデルの各可能な値のために1つ、またはカスタムステップを使用します（数値を指定する場合）。例: `markers` `markers="5"`
      * `dragrange::Bool` - ユーザーは2つのサムだけでなく範囲をドラッグできます
      * `dragonlyrange::Bool` - ユーザーは2つのサムではなく範囲のみをドラッグできます
3. 一般

      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値。例: `0` `100`
4. ラベル

      * `labelcolorleft::String` - 左ラベル背景の色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `labeltextcolorleft::String` - 左ラベルテキストの色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `labelcolorright::String` - 右ラベル背景の色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `labeltextcolorright::String` - 右ラベルテキストの色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `labelvalueleft::Union{String, Int}` - 最小値のデフォルトラベルをオーバーライドします。例: `labelvalueleft="model.min + 'px'"`
      * `labelvalueright::Union{String, Int}` - 最大値のデフォルトラベルをオーバーライドします。例: `labelvalueright="model.max + 'px'"`
5. モデル

      * `range::AbstractRange{T}` - 最小:ステップ:最大の値の範囲。シンボルまたは文字列を使用してモデルフィールドを参照できます。例: `range("min":2:"max", :myvalue)`
      * `lazy::Bool` - trueの場合、スライダーを放すまでモデルフィールドの値を更新しません
6. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
7. スタイル

      * `color::String` - コンポーネントの色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `labelcolor::String` - コンポーネントの色名 [Color Palette](https://quasar.dev/style/color-palette) から。例: `primary` `teal-10`
      * `thumbpath::String` - カスタムサムSVGパスを設定します。例: `M5 5 h10 v10 h-10 v-10`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `dense::Bool` - 密なモード; より少ないスペースを占有します

```
