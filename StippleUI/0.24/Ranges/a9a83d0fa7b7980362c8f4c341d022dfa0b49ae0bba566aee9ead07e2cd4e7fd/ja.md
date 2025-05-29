```
range(range::AbstractRange{<:Union{Symbol, String, Real}}, fieldname::Union{Symbol,Nothing} = nothing, args...; lazy = false, kwargs...)
```

`range` コンポーネントは、ユーザーに最小値と最大値の間の値のサブレンジを選択する機会を提供する素晴らしい方法であり、これらの値を選択するためのオプションのステップを持っています。Range コンポーネントの使用例としては、価格範囲の選択を提供することが挙げられます。

---

### 例

---

### モデル

```julia-repl
julia> @vars RangeModel begin
         range_data::R{RangeData{Int}} = RangeData(18:80)
       end
```

### ビュー

```julia-repl
julia> range(18:1:90,
          :range_data;
          label=true,
          color="purple",
          labelalways=true,
          labelvalueleft=Symbol("'Min age: ' + range_data.min"),
          labelvalueright=Symbol("'Max age: ' + range_data.max")
       )
```

---

### 引数

---

1. 動作

      * `name::String` - コントロールの名前を指定するために使用されます; URL に直接送信されるフォームを扱う場合に便利です ex. `car_id`
      * `snap::Bool` - 有効な値にスナップし、自由にスライドしない; 提案: 'step' プロパティと一緒に使用
      * `reverse::Bool` - 逆方向に動作する（方向を変更）
      * `vertical::Bool` - 垂直方向に表示
      * `labelalways::Bool` - 常にラベルを表示
2. コンテンツ

      * `label::Bool` - ユーザーがスライダーのサムをクリック/タップして移動したときにラベルをポップアップ
      * `markers::Union{Bool, Int}` - トラック上にマーカーを表示し、モデルの各可能な値のために1つ、またはカスタムステップを使用（数値を指定する場合） ex. `markers` `markers="5"`
      * `dragrange::Bool` - ユーザーは2つのサムだけでなく範囲をドラッグできる
      * `dragonlyrange::Bool` - ユーザーは2つのサムではなく範囲のみをドラッグできる
3. 一般

      * `tabindex::Union{Int, String}` - タブインデックス HTML 属性値 ex. `0` `100`
4. ラベル

      * `labelcolorleft::String` - [カラーパレット](https://quasar.dev/style/color-palette) から左ラベル背景の色名 ex. `primary` `teal-10`
      * `labeltextcolorleft::String` - [カラーパレット](https://quasar.dev/style/color-palette) から左ラベルテキストの色名 ex. `primary` `teal-10`
      * `labelcolorright::String` - [カラーパレット](https://quasar.dev/style/color-palette) から右ラベル背景の色名 ex. `primary` `teal-10`
      * `labeltextcolorright::String` - [カラーパレット](https://quasar.dev/style/color-palette) から右ラベルテキストの色名 ex. `primary` `teal-10`
      * `labelvalueleft::Union{String, Int}` - 最小値のデフォルトラベルをオーバーライド ex. `labelvalueleft="model.min + 'px'"`
      * `labelvalueright::Union{String, Int}` - 最大値のデフォルトラベルをオーバーライド ex. `labelvalueright="model.max + 'px'"`
5. モデル

      * `range::AbstractRange{T}` - min:step:max から選択する値の範囲、シンボルまたは文字列を使用してモデルフィールドを参照できます。例: `range("min":2:"max", :myvalue)`
      * `lazy::Bool` - true の場合、スライダーを放すまでモデルフィールドの値を更新しない
6. 状態

      * `disable::Bool` - コンポーネントを無効モードにする
      * `readonly::Bool` - コンポーネントを読み取り専用モードにする
7. スタイル

      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの色名 ex. `primary` `teal-10`
      * `labelcolor::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの色名 ex. `primary` `teal-10`
      * `thumbpath::String` - カスタムサム SVG パスを設定 ex. `M5 5 h10 v10 h-10 v-10`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知
      * `dense::Bool` - 密なモード; より少ないスペースを占有

```
