```
  chatmessage(text::Union{Symbol, Vector{<:AbstractString}, AbstractString} = "", args...; kwargs...)
```

`chatmessage`は、リアクティブモデルによって与えられたデータをレンダリングするチャットエントリです。

---

### 例

---

### モデル

```julia-repl
julia> @app begin
          @out textmsg1 = ["hey, how are you?"]
          @out textmsg2 = "I am good"
          @out messages = Dict{Symbol, Any}[]
       end
```

### ビュー

```julia-repl
julia> chatmessage("This is static text", name="stella", sent = true)
julia> chatmessage(:textmsg1, name="dave", sent = true)
julia> chatmessage(Symbol("[textmsg2]"), name="stella")
julia> chatmessage(R"message.text", name = R"message.name", sent = R"message.sent", "", @for("message in messages"))
```

---

### 引数

---

1. 挙動

      * `htmllabel::Bool` - ラベルをHTMLとしてレンダリングします。これによりXSS攻撃が発生する可能性があるため、メッセージを最初にサニタイズすることを確認してください。
      * `htmlname::Bool` - 名前をHTMLとしてレンダリングします。これによりXSS攻撃が発生する可能性があるため、メッセージを最初にサニタイズすることを確認してください。
      * `htmlstamp::Bool` - テキストをHTMLとしてレンダリングします。これによりXSS攻撃が発生する可能性があるため、メッセージを最初にサニタイズすることを確認してください。
      * `htmltext::Bool` - スタンプをHTMLとしてレンダリングします。これによりXSS攻撃が発生する可能性があるため、メッセージを最初にサニタイズすることを確認してください。
2. コンテンツ

      * `send::Bool` - 送信されたメッセージとしてレンダリングします（現在のユーザーからのもの）。
      * `label::String` - ラベルヘッダー/セクションのみをレンダリングします。例 `Friday, 18th`
      * `name::String` - 著者の名前。例 `John Doe`。
      * `avatar::String` - 著者のアバター画像のURL。例 `(public folder) src="boy-avatar.png"` | `(assets folder) src="~assets/boy-avatar.png"` | `(relative path format) :src="require('./my_img.jpg')"` | `(URL) src="https://placeimg.com/500/300/nature"`
      * `text::Union{AbstractString, Vector{<:AbstractString}}` - メッセージ本文の文字列の配列。文字列はサニタイズされません（詳細はドキュメントを参照）。
      * `stamp::String` - 作成タイムスタンプ。例 `13:55` `Yesterday at 13:51`
3. スタイル

      * `bgcolor::String` - チャットバブルの背景色の名前（Quasar Color Paletteから）。
      * `textcolor::String` - チャットバブルのテキスト色の名前（Quasar Color Paletteから）。
      * `size::String` - 1-12の範囲で12（col-*と同じ）。
