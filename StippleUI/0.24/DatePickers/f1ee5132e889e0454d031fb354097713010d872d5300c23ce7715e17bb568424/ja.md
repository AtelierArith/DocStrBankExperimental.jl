```
datepicker()
```

日付ピッカー（カレンダー）入力要素をレンダリングします。`fieldname`が`Vector{Date}`を参照する場合、`multiple`キーワードパラメータを`true`として渡す必要があります。`fieldname`が`DateRange`を参照する場合、`range`キーワードパラメータを`true`として渡す必要があります。`fieldname`が`Vector{DateRange}`を参照する場合、`multiple`と`range`の両方のキーワードパラメータを`true`として渡す必要があります。

---

### 例

---

### モデル

```julia-repl
julia> @vars DatePickers begin
        date::R{Date} = today() + Day(30)
        dates::R{Vector{Date}} = Date[today()+Day(10), today()+Day(20), today()+Day(30)]
        daterange::R{DateRange} = DateRange(today(), (today() + Day(3)))
        dateranges::R{Vector{DateRange}} = [
          DateRange(today(), (today() + Day(3))),
          DateRange(today() + Day(7), (today() + Day(10))),
          DateRange(today() + Day(14), (today() + Day(17))),
        ]
        proxydate::R{Date} = today()
        inputdate::R{Date} = today()
      end
```

### ビュー

```julia-repl
julia> datepicker(:date)
julia> datepicker(:dates, multiple = true)
julia> datepicker(:daterange, range = true)
julia> datepicker(:dateranges, range = true, multiple = true)
```

---

### 引数

---

1. 動作

      * `name::String` - コントロールの名前を指定するために使用されます; URLに直接送信されるフォームを扱う場合に便利です ex. `"car_id"`
      * `landscape::Bool` - コンポーネントを横向きモードで表示
      * `yearsinmonthview::Bool` - 月表示で年のセレクタを表示
2. コンテンツ

      * `title::String` - 指定された場合、デフォルトのヘッダータイトルを上書きします; 'minimal'モードでない場合に意味があります ex. `"Birthday"`
      * `subtitle::String`  - 指定された場合、デフォルトのヘッダーサブタイトルを上書きします; 'minimal'モードでない場合に意味があります ex. `"John Doe"`
      * `todaybtn::Bool` - 現在の日を選択するボタンを表示
      * `minimal::Bool` - ヘッダーを表示しない
3. 選択

      * `navminyearmonth::String` - 特定の年+月（YYYY/MM形式）以下にナビゲートできないようにユーザーをロックします; このプロパティはモデルを修正するためには使用されません; 'default-year-month'プロパティも使用することをお勧めします ex. `"2020/07"`
      * `navmaxyearmonth::String` - 特定の年+月（YYYY/MM形式）以上にナビゲートできないようにユーザーをロックします; このプロパティはモデルを修正するためには使用されません; 'default-year-month'プロパティも使用することをお勧めします ex. `"2020/10"`
      * `nounset::Bool` - 日付を選択解除する能力を削除します; すでに選択された日付の範囲を選択することには適用されません
      * `multiple::Bool` - 複数選択を許可します; モデルは配列でなければなりません
      * `range::Bool` - 範囲選択を許可します; 'options'プロパティとの部分的な互換性: 選択された範囲には'選択不可'の日も含まれる可能性があります
4. 状態

      * `readonly::Bool` - コンポーネントを読み取り専用モードにします
      * `disable::Bool` - コンポーネントを無効モードにします
5. スタイル

      * `color::String` - Quasarカラーパレットからのコンポーネントの色名 ex. `"primary"` `"teal-10"`
      * `textcolor::String` - テキストの色を上書きします（必要な場合）; Quasarカラーパレットからの色名 ex. `"primary"` `"teal-10"`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `square::Bool` - ボーダー半径を削除してボーダーを四角くします
      * `flat::Bool` - 'フラット'デザインを適用します（デフォルトの影なし）
      * `bordered::Bool` - コンポーネントにデフォルトのボーダーを適用します
      * `eventcolor::String` - 色名（Quasarカラーパレットから）; 関数を使用する場合、日付を文字列として受け取り、文字列を返す必要があります（受け取った日付の色）; 関数を使用する場合は、最良のパフォーマンスのためにスコープから参照し、インラインで定義しないでください ex. `"teal-10"` `eventcolor!="(date) => date[9] % 2 === 0 ? 'teal' : 'orange'"`
