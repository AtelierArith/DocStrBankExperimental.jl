```
tabpanelgroup(args...; kwargs...)
```

`timepicker`コンポーネントは、時間を入力するためのメソッドを提供します。

---

### 例

---

### モデル

```julia-repl
julia> @vars TabPanelModel begin
         time::R{Time} = Dates.Time(t -> Dates.minute(t) == 20, 23)
         timewithseconds::R{Time} = Dates.Time(t -> Dates.second(t) == 12, 20, 23)
       end
```

### ビュー

```julia-repl
julia> Html.div(class="q-gutter-md", [
         timepicker(:time, mask="HH:mm"),
         timepicker(:timewithseconds, mask="HH:mm:ss")
       ])
```

---

### 引数

---

1. 動作

      * `name:String` - コントロールの名前を指定するために使用されます; URLに直接送信されるフォームを扱う場合に便利です
      * `landscape::Bool` - コンポーネントを横向きモードで表示します
      * `format24h::Bool` - AM/PMシステムの代わりに24時間表示を強制します
      * `options::String` - ユーザーが設定できる時間をオプションで構成します; 'hour-options'、'minute-options'、および 'second-options'が設定されている場合はそれらによって上書きされます; 最良のパフォーマンスのために、スコープから参照し、インラインで定義しないでください。例: `options!="(hr, min, sec) => hr <= 6"`
      * `optionshour::Array` - ユーザーが設定できる時間をオプションで構成します; それが設定されている場合は 'options' プロパティを上書きします。例: `optionshour! ="[3,6,9]"`
      * `optionsminute::Array` - ユーザーが設定できる分をオプションで構成します; それが設定されている場合は 'options' プロパティを上書きします。例: `optionsminute! ="[3,6,9]"`
      * `optionssecond::Array` - ユーザーが設定できる秒をオプションで構成します; それが設定されている場合は 'options' プロパティを上書きします。例: `optionssecond! ="[3,6,9]"`
      * `withseconds::Bool` - 秒を含めて時間を設定できるようにします
2. コンテンツ

      * `nowbtn::Bool` - 現在の時間を選択するボタンを表示します
3. モデル

      * `mask::String` - 値の解析とフォーマットに使用されるマスク（フォーマット文字列）例: `HH:mm:ss`
      * `withseconds::Bool` - 秒を含めて時間を設定できるようにします
4. 状態

      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
      * `disable::Bool` - コンポーネントを無効モードにします
5. スタイル

      * `color::String` - カラーパレットからのコンポーネントの色
      * `textcolor::String` - テキストの色を上書きします（必要に応じて）; Quasar Color Paletteからの色名
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `square::Bool` - ボーダー半径を削除してボーダーを四角くします
      * `flat::Bool` - 'フラット'デザインを適用します（デフォルトの影なし）
      * `bordered::Bool` - コンポーネントにデフォルトのボーダーを適用します

```
